---
title: "new gmail-notifier with proxy support"
date: 2006-07-19
forum: Programming Talk
---

### Post by j.vimal on 2006-07-19
Hi
I have written a small gmail-notifier in Python, which only has proxy support now :) 
The problem is, I am behind a proxy, and I sniffed out what the Firefox extension does, and coded my program accordingly. I don't know how the connection goes (SSL) in case there is no proxy, so, I didn't code it as of now.
Anyway, if you are not behind a proxy, you can use the already available gmail-notifier! That one doesn't have proxy support.

This is the program, I have attached the tar.bz2 file ... extract it and go to the same folder, and then run it from the terminal. I am working on running it from anywhere ... this is because the glade files are not loaded :)
So, for the time being run the program from a script file... like this...

```

#!/bin/bash
cd path/to/gmail-notifier
python gmail-ui.py

```
You can also create a custom application launcher, and run the above script. The icon will come to the Notification Area.

Password saving is a little bit secure, in the sense, the person who knows how it is stored will be easily able to decrypt it. So, saving passwords is upto you... 

It is also better to run the program from the terminal, I like the ouput it gives :)

Pre-configuring:
1. make a directory called .gmail-notifier in your home directory
2. Create a file "proxy" with the text **proxy_host:the_proxy_port**

```

mkdir ~/.gmail-notifier
cd ~/.gmail-notifier
echo 'proxy.com:3128' > proxy

```

Now:
How to use:
1. Left click the icon in the tray to show the list of mails.
2. Double click (left click) to check the mail again.
3. Middle click to open the options window
4. Right click to exit


Any bug-reports welcome :)

Note: Only proxy support now!

---

