---
title: "POST in Java vs Python"
date: 2010-04-15
forum: Programming Talk
---

### Post by skullmunky on 2010-04-15
I have some pretty straightforward code in python using a POST request, and want to do the same in Java.  The python version works fine, but the Java version gives me a 500 server error when I do connection.getInputStream().  What's python able to handle that Java isn't handling?

```

#python version
import httplib,urllib

params=urllib.urlencode ( {'food':'cheese','taste':'yummy'})

headers={"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}
conn = httplib.HTTPConnection("www.mysite.com")
conn.request("POST","/myscript.php",params,headers)
response=conn.getresponse()
print response.status, response.reason
data=response.read()
print data
conn.close()

```

```

URL url;

try {
    url = new URL("http://mysite.com/myscript.php");

    HttpURLConnection connection = (HttpURLConnection) url.openConnection();

    connection.setRequestMethod("POST");
    connection.setDoOutput(true);
    connection.setDoInput(true);

    connection.setRequestProperty
    ("Content-Type", "application/x-www-form-urlencoded");


    println("opened connection");

    OutputStreamWriter out = new OutputStreamWriter(connection.getOutputStream(),"UTF-8");
    out.write(URLEncoder.encode("food=cheese&taste=yummy","UTF-8"));
    out.flush();
    out.close();

    BufferedReader in = new BufferedReader(new InputStreamReader(connection.getInputStream()));

    String inputLine;

    while ((inputLine = in.readLine()) != null)
        System.out.println(inputLine);
    
    in.close();

} catch (MalformedURLException ex) {
        ex.printStackTrace();
    } catch (IOException ex) {
        ex.printStackTrace();
    }

```

The line it dies on is
```

BufferedReader in = new BufferedReader(new InputStreamReader(connection.getInputStream()));

```

```

java.io.IOException: Server returned HTTP response code: 500 for URL: http://mysite.com/myscript.php

```

---

### Post by Some Penguin on 2010-04-15
I suspect that you're URL-encoding the parameter string as a single string, instead of URL encoding just the parameters.  That would turn your ampersand into an encoded ampersand.

---

### Post by slavik on 2010-04-15
Another thing, please write out some kind of message before you print a stack trace ...

---

### Post by skullmunky on 2010-04-19
Bingo.  Thanks!

---

