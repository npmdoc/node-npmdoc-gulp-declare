# api documentation for  [gulp-declare (v0.3.0)](https://github.com/lazd/gulp-declare)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-declare.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-declare) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-declare.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-declare)
#### Safely declare namespaces and set their properties

[![NPM](https://nodei.co/npm/gulp-declare.png?downloads=true)](https://www.npmjs.com/package/gulp-declare)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-declare/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-gulp-declare_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-declare/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-gulp-declare/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-gulp-declare/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Larry Davis",
        "email": "lazdnet@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/lazd/gulp-declare/issues"
    },
    "dependencies": {
        "nsdeclare": "^0.1.0",
        "vinyl-map": "^1.0.1",
        "xtend": "^4.0.0"
    },
    "description": "Safely declare namespaces and set their properties",
    "devDependencies": {
        "gulp-util": "^3.0.0",
        "mocha": "^1.21.4",
        "should": "^4.0.4"
    },
    "directories": {},
    "dist": {
        "shasum": "86830fc6faa88e06382162c8664b8e94957afcd9",
        "tarball": "https://registry.npmjs.org/gulp-declare/-/gulp-declare-0.3.0.tgz"
    },
    "engines": {
        "node": ">=0.10"
    },
    "homepage": "https://github.com/lazd/gulp-declare",
    "keywords": [
        "gulpplugin",
        "declare"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "lazd",
            "email": "lazdnet@gmail.com"
        }
    ],
    "name": "gulp-declare",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/lazd/gulp-declare.git"
    },
    "scripts": {
        "test": "mocha"
    },
    "version": "0.3.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module gulp-declare](#apidoc.module.gulp-declare)
1.  [function <span class="apidocSignatureSpan">gulp-declare.</span>processNameByPath (filePath)](#apidoc.element.gulp-declare.processNameByPath)



# <a name="apidoc.module.gulp-declare"></a>[module gulp-declare](#apidoc.module.gulp-declare)

#### <a name="apidoc.element.gulp-declare.processNameByPath"></a>[function <span class="apidocSignatureSpan">gulp-declare.</span>processNameByPath (filePath)](#apidoc.element.gulp-declare.processNameByPath)
- description and source-code
```javascript
processNameByPath = function (filePath) {
  // Make the directory relative
  filePath = path.relative(process.cwd(), filePath);

  // Split the path into its components based on the separator
  var parts = filePath.split(path.sep);

  // Remove and process template name
  var templateName = path.basename(parts.pop(), '.js');

  // Add template name back
  parts.push(templateName);

  // Turn the path into dot notation
  return parts.join('.');
}
```
- example usage
```shell
...
'''js
module.exports["App"] = module.exports["App"] || {};
module.exports["App"]["Main"] = /* File contents from App.Main.js */;
module.exports["App"]["Header"] = /* File contents from App.Header.js */;
module.exports["App"]["Footer"] = /* File contents from App.Footer.js */;
'''

### declare.processNameByPath(filePath)

Pass this method as 'options.processName' so the path within the namespace matches the path in the filesystem combined with dot
notation from the filename:

'''js
gulp.src(['templates/**/*.html'])
.pipe(domly()) // Compile HTML to document fragment builder functions
.pipe(declare({
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
