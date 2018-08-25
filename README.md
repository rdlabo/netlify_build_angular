[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)

# Netlify's build file for Angular Project

This file is Netlify's build file for Angular Project. You can set your environment to this file auto. This will help to increase the lighthouse's score

This file build for 4 method.
1. create `robot.txt`.
2. create `_redirects` for redirect to www.
3. create `_headers` for ServerPush.
4. change styles inline.

If you use this file, you put this file in package.json's directory.
And in Netlify's deploy setting, add Build command `node netlify.build.js`

## How to use
Put `netlify.build.js` in `package.json`'s directory. 
And in Netlify's deploy setting, add Build command `node netlify.build.js`

## example create file

### create `robot.txt`.
If your robots.txt file is malformed, crawlers may not be able to understand how you want your website to be crawled or indexed.
```
User-Agent: *
Allow: /
Host: rdlabo.jp
```

### create `_redirects` for redirect to www.
You can use naked domains with Netlify, but we recommend you always use the www version of the domain (eg. www.example.com) for your site. This makes it easier to take advantage of Netlify’s powerful CDN.
```
https://rdlabo.jp/*  https://www.rdlabo.jp/:splat  301
/* /index.html 200
```

### create `_headers` for ServerPush.
HTTP/2 server push is a performance optimization included in version 2 of the HTTP protocol.
```
/*
  Link: <main.f1ec16ef52a78f4177f7.js>; rel=preload; as=script
  Link: <polyfills.2f4a59095805af02bd79.js>; rel=preload; as=script
  Link: <runtime.a66f828dca56eeb90e02.js>; rel=preload; as=script
```

### change styles inline.
Resources are blocking the first paint of your page. Consider delivering critical JS/CSS inline and deferring all non-critical JS/styles.
```index.html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Default</title>
  <base href="/">

  <meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="google-site-verification" content="H5ph58N7a9jJVFaL63YKNA5lQsM77jcqd5pSFv18I_I" />
  <link rel="icon" type="image/x-icon" href="favicon.ico"><style></style></head>
<body>
  <app-root></app-root>
<script type="text/javascript" src="runtime.a66f828dca56eeb90e02.js"></script><script type="text/javascript" src="polyfills.2f4a59095805af02bd79.js"></script><script type="text/javascript" src="main.f1ec16ef52a78f4177f7.js"></script></body>
</html>
```
