---
title: "custom libraries"
date: 2007-05-08
forum: Programming Talk
---

### Post by Bobtheknight on 2007-05-08
My betters,

I have a java file that starts with this the following attatched at bottom (shortened).  I wish to write code that uses this file like a library.  Ie.  ClientHttpRequest client = new ClientHttprequest;  client.function(); and so on.  But what I have is not the normal .jar that's all compiled and nice that I can throw in my library and set -classpath to.  I have a source file.

Can someone tell me how to build this into a library I can import and call?

package com.myjavatools.web;



import java.net.URLConnection;

import java.net.URL;

import java.io.IOException;

import java.util.HashMap;

import java.util.Map;

import java.io.File;

import java.io.InputStream;

import java.util.Random;

import java.io.OutputStream;

import java.io.FileInputStream;

import java.util.Iterator;



/**

 * <p>Title: Client HTTP Request class</p>

 * <p>Description: this class helps to send POST HTTP requests with various form data,

 * including files. Cookies can be added to be included in the request.</p>

 *

 * @author Vlad Patryshev

 * @version 1.0

 */

public class ClientHttpRequest {

---

