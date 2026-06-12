---
title: "http post in java not returning getting the weather"
date: 2008-09-19
forum: Programming Talk
---

### Post by go_beep_yourself on 2008-09-19
I want to use this code I got from here  [http://exampledepot.com/egs/java.net/Post.html](http://exampledepot.com/egs/java.net/Post.html) 

```
    try {
        // Construct data
        String data = URLEncoder.encode("key1", "UTF-8") + "=" + URLEncoder.encode("value1", "UTF-8");
        data += "&" + URLEncoder.encode("key2", "UTF-8") + "=" + URLEncoder.encode("value2", "UTF-8");
    
        // Send data
        URL url = new URL("http://hostname:80/cgi");
        URLConnection conn = url.openConnection();
        conn.setDoOutput(true);
        OutputStreamWriter wr = new OutputStreamWriter(conn.getOutputStream());
        wr.write(data);
        wr.flush();
    
        // Get the response
        BufferedReader rd = new BufferedReader(new InputStreamReader(conn.getInputStream()));
        String line;
        while ((line = rd.readLine()) != null) {
            // Process line...
        }
        wr.close();
        rd.close();
    } catch (Exception e) {
    }
```

to submit a zip code to this site  [http://weather.yahoo.com/](http://weather.yahoo.com/) . Where did i go wrong in my code? 

```
import java.util.*;
import java.io.*;
import java.net.*;
public class Weather {
  public static void main(String[] args) throws Exception {
   //try {
        // Construct data
        String data = URLEncoder.encode("ptrigger2", "UTF-8") + "=" + URLEncoder.encode("10027", "UTF-8");
 
        // Send data
        URL url = new URL("http://weather.yahoo.com/search/weather2");
        URLConnection conn = url.openConnection();
        conn.setDoOutput(true);
        OutputStreamWriter wr = new OutputStreamWriter(conn.getOutputStream());
        wr.write(data);
        wr.flush();
 
        // Get the response
        BufferedReader rd = new BufferedReader(new InputStreamReader(conn.getInputStream()));
        String line;
        while ((line = rd.readLine()) != null) {
            System.out.println(line);
        }
        wr.close();
        rd.close();
    //} catch (Exception e) {
    //}
  }
}
```

rd.readLine() in that last while loop is returning null.

---

### Post by tinny on 2008-09-19
Your code works for me. (I have attached the result)

Maybe you need to call the "ready" method of the BufferedReader.

E.g

[PHP]
        while (!rd.ready()) {
            Thread.sleep(100);
        }
        
        String line;
        
        while ((line = rd.readLine()) != null) {
            System.out.println(line);
        }
[/PHP]

---

### Post by go_beep_yourself on 2008-09-27
Actually I had been getting the same result as you, and if you change that result.txt to result.html and open in Firefox, you'll see that the weather for the zip code was not retrieved. Thanks for the suggestion anyhow. I was able to make that code work for noaa.org.

---

