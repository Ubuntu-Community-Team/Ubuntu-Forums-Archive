---
title: "help with java (JSCSSMergeServlet)"
date: 2011-01-16
forum: Programming Talk
---

### Post by mikejonesey on 2011-01-16
I'm trying to incorporate a little more code into a java class;

[http://code.google.com/p/webutilities/](http://code.google.com/p/webutilities/)

JSCSSMergeServlet.java

I'd like to be able to include css and js files from multiple directories; i've written the extra code, I'm using eclipse javaee - IDE.

The problem is I can't seem to get the compiler to process the additional code (the .jar seems to overwrite it; am I missing classes, how do I get my @overide to work...)

cheers for any help

```
package com.googlecode.webutilities;

import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.StringWriter;
import java.io.Writer;
import java.util.Collections;
import java.util.Date;
import java.util.LinkedHashMap;
import java.util.Map;

import javax.servlet.ServletConfig;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class JSCSSMergeServlet extends HttpServlet{

        private static final long serialVersionUID = 1L;
        
        private long expiresMinutes = 7*24*60; //+ or - minutes to be added as expires header from current time. default 7 days
        
        private boolean useCahce = true;
        
        private Map<String, String> cache = Collections.synchronizedMap(new LinkedHashMap<String, String>());
        
        @Override
        public void init(ServletConfig config) throws ServletException {
                super.init(config);
                this.expiresMinutes = ifValidNumber(config.getInitParameter("expiresMinutes"), this.expiresMinutes);
        }
        
        private String addHeaders(HttpServletRequest req,HttpServletResponse resp)
        {
                String url = req.getRequestURI().toLowerCase();
                if(url.endsWith(".json"))
                {
                    resp.setContentType("application/json");
                }
                else if(url.endsWith(".js"))
                {
                        resp.setContentType("text/javascript");
                }
                else if(url.endsWith(".css"))
                {
                        resp.setContentType("text/css");
                }
                resp.addDateHeader("Expires", new Date().getTime() + expiresMinutes*60*1000);
                resp.addDateHeader("Last-Modified", new Date().getTime());
                return url;
        }
        
        private void expireCache()
        {
                this.cache.clear();
        }
        
        protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException
        {
                String path, file;
                String url = addHeaders(req, resp);
                if(req.getParameter("_expirecache_") != null){
                        this.expireCache();
                }
                boolean useCache = this.useCahce && req.getParameter("_skipcache_") == null && req.getParameter("_dbg_") == null;
                
                if(useCache){
                        String fromCache = cache.get(req.getRequestURI());
                        if(fromCache != null){
                                Writer writer = resp.getWriter();
                                writer.write(fromCache);
                                writer.flush();
                                writer.close();
                                return;
                        }
                }
                
                url = url.replace(req.getContextPath(), "");
                
                if(url.contains(","))
                {
                    path = url.substring(0,url.indexOf(","));
                    path = super.getServletContext().getRealPath(path.substring(0,path.lastIndexOf("/")));
                    file = url.replaceAll(path+"/", "");
                }
                else
                {
                    path = super.getServletContext().getRealPath(url.substring(0,url.lastIndexOf("/")));
                    file = url.replaceAll(path+"/", "");
                }
                
                Writer out = new StringWriter();
                if(!useCache){
                        out = resp.getWriter();
                }
                String[] files = file.split(",");
                String fullPath = null;
                for(String f : files){
                        if(url.endsWith(".json") && !f.endsWith(".json")){
                                f += ".json";
                        }
                        if(url.endsWith(".js") && !f.endsWith(".js")){
                                f += ".js";
                        }
                        if(url.endsWith(".css") && !f.endsWith(".css")){
                                f += ".css";
                        }
                        
                        if(!f.contains("/"))
                        {
                            fullPath = path + File.separator + f;
                        }
                        else
                        {
                            String tmppath = f.substring(0,f.indexOf(","));
                            tmppath = super.getServletContext().getRealPath(tmppath.substring(0,tmppath.lastIndexOf("/")));
                            fullPath = tmppath + File.separator + f;
                        }
                        
                        FileInputStream fis = null;
                        try{
                                File fl = new File(fullPath);
                                fis = new FileInputStream(fl);
                                int c;
                                while((c = fis.read()) != -1){
                                        out.write(c);
                                }
                                out.flush();
                        }catch (Exception e) {
                                
                                log("Exception in "+"["+fullPath+"]"+JSCSSMergeServlet.class.getSimpleName()+":" + e);
                                
                        }finally{
                                if(fis != null){
                                        fis.close();
                                }
                                if(out != null){
                                        out.close();
                                }
                        }
                        
                }
                if(useCache){
                        cache.put(req.getRequestURI(), out.toString());
                        resp.getWriter().write(out.toString());
                }
                req.getRequestDispatcher("/googleWebutilities.jsp").forward(req,resp);
        }
        
        private long ifValidNumber(String s, long def){
                if(s != null && s.matches("[0-9]+")){
                        try{
                                return Long.parseLong(s);
                        }catch (Exception e) {
                                return def;
                        }
                }
                return def;
        }
}
```

---

