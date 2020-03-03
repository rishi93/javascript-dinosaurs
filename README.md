# Javascript for dinosaurs
## Step 1
Create a new folder for your project
```bash
mkdir mysite && cd mysite
```
## Step 2
Initialize npm for this project
```bash
npm init
```
If you follow all the instructions, a *package.json* file will be created
## Step 3
Write some HTML, CSS. Write some JS in index.js and link to the HTML by
```html
<!-- some HTML content -->
<script src='index.js'></script>
```
## Step 4
Install some modules
```bash
npm install moment --save
```
The package name is saved as a dependency in *package.json* file  
The source code is downloaded to *node_modules* folder  
## Step 5
```bash
npm install webpack webpack-cli --save-dev
```
Create a *webpack.config.js* file
```javascript
module.exports = {
    mode: 'development',
    entry: './index.js',
    output: {
        publicPath: 'dist',
        filename: 'main.js'
    }
}
```
## Step 6
Install a transpiler for the latest JS features
```bash
npm install @babel/core @babel/preset-env babel-loader --save-dev
```
@babel/core is the main part of babel  
@babel/preset-env is a preset defining which new features of JS to transpile  
babel-loader is a package to enable babel to work with webpack  
Make the following changes to the *webpack.config.js* file
```javascript
module: {
    rules: [
        {
            test: /\.js$/,
            exclude: /node_modules/,
            use: {
                loader: 'babel-loader',
                options: {
                    presets: ['@babel/preset-env']
                }
            }
        }
    ]
}
```
## Step 7
Install webpack-dev-server to watch changes
```bash
npm install webpack-dev-server --save-dev
```
Add the following scripts to the *package.json* file
```javascript
"scripts": {
    "build": "webpack --progress --mode=production",
    "server": "webpack-dev-server --open"
}
```
Now you can build the *dist/main.js* file by running
```
npm run build
```
and run the webserver by
```
npm run server
```