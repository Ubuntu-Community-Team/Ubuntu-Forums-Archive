---
title: "WebLogic 10 installation guide"
date: 2008-03-08
forum: Programming Talk
---

### Post by brian.pedersen on 2008-03-08
Just wanted to share my experiences on this.

1. Make sure you have the sun-java5-jdk installed, other JDK's might work but Sun 1.5 is a safe choice
2. Go to [http://dev2dev.bea.com/wlserver](http://dev2dev.bea.com/wlserver) in a browser and click the download link
3. When prompted for an OS selection, choose the Suse download as this is a generic .jar installer
4. when the download has completed, you might want to browse the installation instructions at [http://e-docs.bea.com/common/docs100/install/start.html#wp1071876](http://e-docs.bea.com/common/docs100/install/start.html#wp1071876)
5. Open a terminal and navigate to the downloaded server10xx_generic.jar and run a console installation by typing java -jar server10xx_generic.jar -mode=console
6. Go for default settings all the way, or perform whatever changes desired
7. If you chose to do a complete installation in the previous step, you can easily verify that the installation was successful after the installation is complete, do this by navigating to your $beahome and start the workshop example server by running $beahome/wlserver_10.0/samples/domains/workshop/startWebLogic.sh in a terminal
8. Once the server prints <Server started in RUNNING mode> in the terminal, you can open [http://127.0.0.1:7001/console](http://127.0.0.1:7001/console) in a browser and log in using the default weblogic/weblogic credentials

It seems the installer does not do a full installation of WebLogic Workshop, but only installs the Workshop specific eclipse plugins.
Running Workshop will therefore involve a few extra steps, I am currently looking into this.

/Brian

---

### Post by brian.pedersen on 2008-03-08
I found the easiest way to get workshop up and running was to actually download the latest version at [http://commerce.bea.com/showproduct.jsp?family=WLW&major=10.2&minor=0](http://commerce.bea.com/showproduct.jsp?family=WLW&major=10.2&minor=0) and do an installation in which I choose to use the bundled Eclipse.

Being unable to start Workshop after the installation completed, I realized why I was also unsuccessful at doing graphical installations of the server, it seems there is a bug in the JDK as described here: [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373) which makes awt broken.

There is an easy workaround described in the bottom of the linked bug report, which basically is about putting in the following line in top of the start script:
```
export LIBXCB_ALLOW_SLOPPY_LOCK=1
```

/Brian

---

### Post by pradeepmodukuri on 2010-04-07
hi guys..
Thank you so much for you help i am very new to ubuntu and wanted to install weblogic 10.3 and downloaded {.bin} file from bea site..

can you plz tell me wht is the command for  installation..and brief process..

Thank you..

---

### Post by lisati on 2010-04-07
The information in this old thread is out of date. Oracle has purchased BEA: see [here]("http://www.oracle.com/bea/index.html").

The correct download link is [here]("http://www.oracle.com/technology/software/products/middleware/index.html")

---

