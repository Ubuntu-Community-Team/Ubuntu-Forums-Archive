---
title: "Converting a python script to java for android"
date: 2009-09-24
forum: Programming Talk
---

### Post by exutable on 2009-09-24
Hello,

I wrote a python script to pull my telmore usage(danish cellular provider), I was wondering what processes I should use to convert this to Java, for use in an android app.  What libraries etc?

Please also comment if I have written something ineffectively, wrong practice etc.

Code is of course released under GPLv2:
```
import urllib
import urllib2
import sys
import cookielib
import hashlib
from BeautifulSoup import BeautifulSoup

#Accept cookies to browse telmore website
cookieJar = cookielib.LWPCookieJar()
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookieJar))

#Add headers
opener.addheaders = [('User-agent', "Mozilla/5.0")]

#Accept arguments for username and password
username = sys.argv[1]
password = sys.argv[2]

#Url requests, first page is login, second is a frame of the login page
url = "https://www.telmore.dk/t2/j_security_check"
url2 = "https://www.telmore.dk/t2/mytelmore/index.do"

#Fill the forms with the username and password arguments
form = { "j_username" : username,
         "j_password" : password }

#Encode the form and create request		 
encodedForm = urllib.urlencode(form)
request = urllib2.Request(url, encodedForm)
page = opener.open(request)

#Request the second page
request = urllib2.Request(url2)
page = opener.open(request)
contents = page.read()

#Beatiful soup to parse the html and sort out the span tag with class saldo
soup = BeautifulSoup(contents)
saldospan = soup.findAll('span')
saldo = saldospan[0].contents[0].strip()
print saldo

```

---

### Post by fishy6969 on 2009-09-24
Out of interest, have you tried running this under the Android Scripting Environment (available from the Market?)

As an alternative a free program in the Market to do the same is NetCounter.

---

### Post by exutable on 2009-09-24
The scripting environment wasn't in the market, I'll look for it in a little from external sources.

The script doesn't watch net usage, it grabs the amount of money you have left on the account.

---

### Post by fishy6969 on 2009-09-24
Sorry it's at [http://code.google.com/p/android-scripting/](http://code.google.com/p/android-scripting/)

> 'it grabs the amount of money you have left on the account'

Great feature!

---

### Post by exutable on 2009-09-24
Thanks buddy,

this looks really good.

---

### Post by exutable on 2009-09-26
So even though I got ASE working, I kind of want to turn this into a real app.  So here is my code so far but it isn't returning anything and I'm pretty sure I'm encoding everything right.

```
import java.net.*;
import java.io.*;

public class TelmoreSaldo {
    public static void main(String[] args) throws Exception {
	try {
        // Construct data
        String data = URLEncoder.encode("j_username", "********") + "=" + URLEncoder.encode("j_password", "**********");
    
        // Send data
        URL url = new URL("https://telmore.dk/t2/j_security_check");
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
    } catch (Exception e) {
    }
}
}
```

---

### Post by exutable on 2009-09-28
bump?

---

### Post by fishy6969 on 2009-09-28
Sorry, Java's not a strong point of mine. You might get more luck asking on one of the Android Developer forums.

Did it work OK under the ASE btw? I've found the ASE to be pretty good.

Regards

---

### Post by exutable on 2009-09-28
Oh yeah totally worked, it was awesome getting Python running.

Yeah I just posted a thread on androidforums.org

[http://androidforums.com/android-developers/10222-converting-python-script-java-android.html]("http://androidforums.com/android-developers/10222-converting-python-script-java-android.html")

---

### Post by Tortel on 2009-09-29
In the catch block, try sticking a e.printStackTrace() to see if theres an exception thats ending it early...

---

### Post by exutable on 2009-09-30
Ahhh Thanks Tortel, I fixed the code and found out what was wrong because of the e.printStackTrace(), thanks.

Here is the revised code:

```
import java.net.*;
import java.io.*;
import javax.swing.text.html.HTML;

public class TelmoreSaldo {
    public static void main(String[] args) throws Exception {
	try {
        // Construct data
        String data = URLEncoder.encode("j_username", "UTF-8") + "=" + URLEncoder.encode("********", "UTF-8") + "&" + URLEncoder.encode("j_password", "UTF-8") + "=" + URLEncoder.encode("********", "UTF-8");
    
        // Send data
        URL url = new URL("https://telmore.dk/t2/j_security_check");
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
        HTML.Tag[] list = HTML.getAllTags();
        for (int i = 0; i < list.length; i++) {
          System.out.println((i + 1) + ": " + list[i]);
        }
        wr.close();
        rd.close();
    } catch (Exception e) {
    	e.printStackTrace();
    }
}
}
```


Now to figure out how to parse the span tag, these parsing libraries are confusing compared to python

---

### Post by Reiger on 2009-09-30
Please note that Java for a desktop is NOT the same as Java for android, and that very likely the nitty-gritty details of connections are taken care of by the underlying platform already if only you use it.

You may want to read: [http://developer.android.com/guide/index.html](http://developer.android.com/guide/index.html)


... If it's just me who is thinking that you wouldn't be using the Android SDK and associated build/develop tools when obviously you are and I am being silly for not realizing it...  feel free to ignore. :P

---

