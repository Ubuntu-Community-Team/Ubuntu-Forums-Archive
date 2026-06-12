---
title: "Java isnt working at all"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by shleyman on 2008-05-20
i have downloaded about a million things and i dont know why it isnt working?
i just removed firefox 3 because it was rubbish, now no java apps arent working at all!
please someone help me 
cheers

edit: I no its a borign title but c'mon all ready im at the bottom of the page with no views!!!!

---

### Post by shleyman on 2008-05-20
I hardly expect anyone to BUMP into this at the bottom....

---

### Post by stchman on 2008-05-20
> **shleyman said:**
> i have downloaded about a million things and i dont know why it isnt working?
i just removed firefox 3 because it was rubbish, now no java apps arent working at all!
please someone help me 
cheers

edit: I no its a borign title but c'mon all ready im at the bottom of the page with no views!!!!

I have Java and it works very well with Firefox 3.  Firefox 3 is awesome.

Did you install the sun-java6-jre and the sun-java6-plugin packages?

Also if you have 64 bit the Java plugin does not work.

---

### Post by NormR2 on 2008-05-20
Go to a Terminal window and enter java -version
Copy the output back here.
If you get a response that looks like the java command has been found and is executing, find a .jar file that is runnable (has a manifest etc) and issue the following:

java -jar <path-jarfile>

Copy the output back here.

---

### Post by shleyman on 2008-05-20
```
ash@the-matrix:~$ java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)
ash@the-matrix:~$ 

```
thats what i get....

---

### Post by shleyman on 2008-05-20
and i dont know if it helps but when i type in about:plugins all i get is shockwave flash and i have everything else installed too...

---

### Post by shleyman on 2008-05-20
and yes i did install whant you said stchman....

---

### Post by uidb4056 on 2008-05-20
I'm running 8.04 64 bits and following this thread i got flash running

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

I've isntalled java OpenJDK and IcedTea from synaptic.

Also I've installed GetLibs to heve compatibility with 32 bits libraries

---

### Post by geoff07 on 2008-05-20
I had a perfectly good java installation under 7.10 and when I installed 8.04 it broke (thanks guys!).

The fix, which took me sometime to figure was the following:

1) install the sun-java6-jre and -plugin packages,plus any related ones that you want.

2) you DO NOT want duplicate apps that cover the same ground, e.g. sun-java5-jre, libgcjwebplugin.so, or gcjwebplugin.so so remove them if they are there

3) you should now have /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so - check it exists

4) create a symlink between firefox and java by:
cd ~/.mozilla/plugins  (if plugins does not exist create it (mkdir plugins)
whilst in the plugin directory, create the link:
ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

you can also try this from the main firefox directory /usr/lib/firefox-xxx/plugins (replace the xxx with your current installation version, you will need to use sudo for this). I'm still not sure which is the best way but you can try each

5) restart firefox and clear the cache (edit/prefs/advanced/network/clear now) 

6) access about: plugins in firefox and check there is only one java plugin enabled

7) search google for 'test java' (java.com/en/download/installed.jsp) and see if the java test shows the dancing symbol. If it does you are done!


Why such a simple thing should be so difficult in 2008 is beyond me, come on developers, this isn't the way to get people off Vista!

---

### Post by NormR2 on 2008-05-20
Your posting shows that the java command is found and seems to be working. 
What is not working?

Can you run a java command at a Terminal and copy the output here that shows the problem?

Or can you describe what program you are running that uses java that isn't working? 

Is it a website with a java applet that you visit in a browser?

---

### Post by keetowah on 2008-05-20
Just go to the package manager and search for Java6.  If there are any broken installs it will tell you, and it will show you which modules are installed.   That's how I've installed it several times without a hitch for FF3 and 2.

---

### Post by shleyman on 2008-05-20
ermm
all i know is that runescape uses java so ive just been on and it give me this error
```
Error_loader_nocache - Unable to create cache directory.
Runescape was unable to find a suitable place to store its temporary files. To solve this please either:

# Login to your computer as an 'administator' user, and then try loading RuneScape again. This should give it sufficient access to create its temporary cache.

# Or, create a new directory called c:/rscache or /rscache. If possible, set that directory to have full read+write permissions so that all users can write to it. Runescape should then detect that directory and use it for its files.

# If you are unable to do either of the above, then as a last resort you can tell RuneScape not to store any files on the harddisk. When entering the site and choosing between high-detail/low-detail also select 'Unsigned Applet Using Default Java' from the dropdown scroll at the bottom of the detail select page. You will need to do this everytime you load the game. The disadvantage of this is the game will load slower, so if possible use one of the top two solutions instead. 
```

could that have something to do with it?

---

### Post by NormR2 on 2008-05-20
sorry, know nothing about runescape

The message you posted seems to say  runescape needs permission to create some files. 

Have you tried what was recommended in the text you posted?
> 
tell RuneScape not to store any files on the harddisk

Have you ever run  runescape successfully on your Ubuntu computer?

Have you tried running it with sudo to give it root authority?

---

