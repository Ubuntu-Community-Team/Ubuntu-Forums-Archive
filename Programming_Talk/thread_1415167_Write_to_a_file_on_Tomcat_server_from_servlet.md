---
title: "Write to a file on Tomcat server from servlet"
date: 2010-02-24
forum: Programming Talk
---

### Post by slogum on 2010-02-24
Hi.

I'm running tomcat. I am trying to write to a txt-file on the server from a servlet, but the txt-file allways end up getting stored in my home-folder.

try {
out = new PrintWriter(new FileWriter("test.txt"));
out.print("This is a text");
out.flush();
out.close();
} catch (IOException e) {
// TODO Auto-generated catch block
e.printStackTrace();
}

When I run this the file "test.txt" is getting stored in my home folder. I've tried a couple of things, like specifying a direct link to where on the server I want it stored, but it still ends up in my home folder.

Like this:
out = new PrintWriter(new FileWriter("/usr/local/tomcat/webapps/app/test.txt"));

This doesent work either.

Any tips? :)

---

### Post by kahumba on 2010-02-24
Try first creating the java.io.File and use the it as a param to the output stream intead of using the path string as param.
This worked for me and created /tmp/myfile.txt with "Today is: Wed Feb 24 21:41:34 EET 2010" in it after visiting the servlet through the browser.

```

 protected void processRequest(HttpServletRequest request, HttpServletResponse response)
    throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        PrintWriter out = response.getWriter();
        try {
//RELEVANT CODE START
            File file = new File("/tmp/myfile.txt");
            file.createNewFile();
            FileOutputStream fout = new FileOutputStream(file);
            fout.write( ("Today is: " + new java.util.Date()).getBytes());
            fout.close();
//RELEVANT CODE END
            out.println("<html>");
            out.println("<head>");
            out.println("<title>Servlet TestFile</title>");  
            out.println("</head>");
            out.println("<body>");
            out.println("<h1>Servlet TestFile at " + request.getContextPath () + "</h1>");
            out.println("</body>");
            out.println("</html>");
        } finally { 
            out.close();
        }
    } 

```

---

