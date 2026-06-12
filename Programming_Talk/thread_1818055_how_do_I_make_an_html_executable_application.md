---
title: "how do I make an html executable application?"
date: 2011-08-04
forum: Programming Talk
---

### Post by kapi on 2011-08-04
Morning all,

Have worked for a business in the past where they used html, javascript etc and converted a website to an html.exe. used for leaning accounting and business. The user downloaded the program and double clicked the exe to start.

I'd like to do something similar but for nurseries but for record keeping.

As I'm an opensource user I was wondering what I could use to develop a stand alone application that runs in a browser.

I code using html, php, javascript, mysql and css. 

Anyone have any advice?

Thanks

---

### Post by hakermania on 2011-08-04
Whola! I've never heard before for 'executable' sites.
I've heard for executables that self-extract and 'create' files (possibly a site, why not?)
Is this what you want to do?

---

### Post by kapi on 2011-08-04
no sorry maybe I was unclear. 

It's an application made with html and javascript etc that runs in a browser. 

Once they have tested the links and forms work then the html code was converted to an html.exe file.

Once clicked it ran as a stand alone app within the browser.

I want to do the same but am unsure how to proceed.

---

### Post by hakermania on 2011-08-04
> **kapi said:**
> no sorry maybe I was unclear. 

It's an application made with html and javascript etc that runs in a browser. 

Once they have tested the links and forms work then the html code was converted to an html.exe file.

Once clicked it ran as a stand alone app within the browser.

I want to do the same but am unsure how to proceed.

Thanks for letting me know that something like this is possible, I thought that you couldn't make an app with HTML, I thought it was pseudo-code... Only for designing things..

---

### Post by Tony Flury on 2011-08-04
The only way i can think of doing this would be to make a self-extracting archive of the html images etc, and design your site in such a way that the site can be viewed by the browser as a local set of files.

Whether you can make self-extracting archives for Linux i am not sure, and if you can it wont be a ".exe" which is of course windows specific.

---

### Post by kapi on 2011-08-04
No worries, thank you for your replies. 

Maybe I'll just look at using another avenue maybe with php or java or something.

---

### Post by PaulM1985 on 2011-08-04
I was thinking of something that was a bit simpler.  The installer puts all the html files in the right place and the "executable" is a program or script which just starts up the users web browser with the appropriate html file as an argument.

Paul

---

### Post by Yuzem on 2011-08-04
> **hakermania said:**
> Thanks for letting me know that something like this is possible, I thought that you couldn't make an app with HTML, I thought it was pseudo-code... Only for designing things..
[Figuritas]("http://yuzem.blogspot.com/p/figuritas-screenshots.html") is made that way.

> **kapi said:**
> No worries, thank you for your replies.

If what you want is a dynamic site you can do what I did for figuritas using thttpd:

```
sudo apt-get install thttpd
```

Then create a file with the following content and make it executable:
```
#!/bin/bash
mySiteFolder=~/mySite

cd $mySiteFolder
thttpd -D -T utf-8 -p 9008 -c '**.cgi' -nos &
xdg-open http://localhost:9008
```

Then by running that file your site should open in the default browser.
All files ending with .cgi will run like programs, for example you can make a file: ~/mySite/index.cgi
And put there:
```

#!/bin/bash
echo Content-type: text/html
echo
echo Hello World!
echo The arguments are $*
```

---

### Post by nvteighen on 2011-08-04
Another possibility would be to write an ad-hoc very lightweight browser that opens those HTML files. I'm pretty sure you can use a GUI toolkit for the basic UI and then ask Gecko or WebKit do the parsing.

---

### Post by cgroza on 2011-08-04
> **nvteighen said:**
> Another possibility would be to write an ad-hoc very lightweight browser that opens those HTML files. I'm pretty sure you can use a GUI toolkit for the basic UI and then ask Gecko or WebKit do the parsing.
That would be very easy. I have seen 50 line Python scripts playing Youtube videos. Webkit takes care of everything. You just need to provide a back/forward button.

---

