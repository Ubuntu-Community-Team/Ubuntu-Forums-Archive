---
title: "HOWTO: Java64 with 64-bit Firefox plugin"
date: 2008-12-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Frak on 2008-12-23
**[CENTER]This tutorial was written specifically for Java 1.6.0_12, but should work fine on future revisions.[/CENTER]**

**Installing Java for 64-bit**

Begin by downloading Java from Sun. [Download Here]("http://download.java.net/jdk6/") **(Linux x64 self-extracting JRE file)**

or paste this command into the terminal:

```
wget -c 'http://www.java.net/download/jdk6/6u12/promoted/b02/binaries/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin'
```

Next, we'll create an install directory in /opt (as this is probably the best place for development applications).

```
cd /opt
sudo mkdir java
cd java
```

Let's copy the installer file to the java directory.

```
sudo cp ~/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin /opt/java/
```

Finally, let's execute the installer

```
sudo bash jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
```

For good measure, let's register this as the default Java provider.

```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/jre1.6.0_12/bin/java" 1
sudo update-alternatives --set java /opt/java/jre1.6.0_12/bin/java
```

**Installing Firefox plugin**
First, lets remove the gcj web plugin:
```
sudo apt-get remove icedtea-gcjwebplugin
```
Remove the Cacao-plugin as described by [Jozza the Wick]("http://ubuntuforums.org/showpost.php?p=7199736&postcount=36"):
```
sudo apt-get remove cacao-oj6-plugin
```
If it comes up with "not found" or the like, ignore it and continue.

Since we have it all setup, all we need to do is install the Firefox plugin. This can be done in one simple command (change according to version).

```
mkdir ~/.mozilla/plugins
ln -s /opt/java/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```

[deepclutch]("http://ubuntuforums.org/showpost.php?p=6655085&postcount=31") reported that this
```
sudo ln -s /opt/java/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib/firefox-3.0.5/plugins/
```
worked instead. If this works for you, and the thanks system comes back up, all credit goes to him/her.


You can test the plugin by restarting your browser and going to [http://www.javatester.org/version.html](http://www.javatester.org/version.html) and checking for the pink box and line of text.

For Epiphany
```
ln -s /opt/java/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib/epiphany-webkit/2.24/plugins/
```
by [deepclutch]("http://ubuntuforums.org/showpost.php?p=6820839&postcount=35")

---

### Post by Nublet on 2008-12-23
i followed the guide, however 
```
./jre-<miscellaneous version information> -amd64-<date>.bin
```
did not work, so i used
```
sudo sh ./jre-<miscellaneous version information> -amd64-<date>.bin
```
instead, and it doesn't work (java doesn't show up in firefox' addons manager, and javatester says it's disabled). did i do it wrong? regardless of wheter it's my fault or not, how can i repair it?

---

### Post by Frak on 2008-12-23
Follow the last part "**Installing Firefox plugin**". And, well, I guess make sure you aren't using the default text I provide, as anything in <> are just placeholders for the actual program. Such as mine was

```
./jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
```

You probably already get that, but for anybody who doesn't, there it is.

---

### Post by SuperSonic4 on 2008-12-23
nice one, java was my last reason for sticking to a 32 bit OS.
Would it be easier to put ```
wget -c 'http://www.java.net/download/jdk6/6u12/promoted/b02/binaries/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin'
``` in the first line though?

---

### Post by Frak on 2008-12-23
> **SuperSonic4 said:**
> nice one, java was my last reason for sticking to a 32 bit OS.
Would it be easier to put ```
wget -c 'http://www.java.net/download/jdk6/6u12/promoted/b02/binaries/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin'
``` in the first line though?
Could, but I find it better if people download the latest build than to stick themselves with just one.

Come to think of it, I'll change it. It could make the guide a bit easier to read.

---

### Post by texadactyl on 2008-12-27
Nice write up.  I told the sun-java maintainer about it as a heads up for future update.  This update actually works at [http://www.pogo.com]("http://www.pogo.com")

BTW, never try to predict ("should work...") the future unless you have a crystal ball that's in good shape!  :popcorn:

---

### Post by Frak on 2008-12-27
> **lemon8h8ead said:**
> Nice write up.  I told the sun-java maintainer about it as a heads up for future update.  This update actually works at [http://www.pogo.com]("http://www.pogo.com")

BTW, never try to predict ("should work...") the future unless you have a crystal ball that's in good shape!  :popcorn:
Thanks, and my crystal ball only has a few cracks ;)

---

### Post by Murrquan on 2009-01-05
How do you undo this and change IcedTea to be the default, again? I installed Sun Java, but Runescape still won't run under it. ^.^;

---

### Post by Frak on 2009-01-05
run sudo update-alternatives java and choose the one you want.

---

### Post by Murrquan on 2009-01-05
Okay ... *does so* It just tells me

```
update-alternatives: unknown argument `java'
```

---

### Post by Frak on 2009-01-05
Sorry,

sudo update-alternatives --config java
and
sudo update-alternatives --config javac

---

### Post by raypsi on 2009-01-10
libnpjp2.so

    File name: libnpjp2.so

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_12 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_12 	Java 		Yes
application/x-java-vm-npruntime 	Java 		Yes

Is what I gots under about:plugins

But it don't worky. I go to the test java web page and it's says it don't work.

**Help says I gots this: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.19) Gecko/20081216 Ubuntu/8.04 (hardy) Firefox/2.0.0.19**

I downloaded this from a java https page: 

**/home/ray/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin**

when I installed it, it showed up here: /home/ray/jre1.6.0_12

and I linked to **/usr/lib64/mozilla-firefox/plugins**

 using:

** sudo ln -s /home/ray/jre1.6.0_12/lib/amd64/libnpjp2.so**

In a terminal at /usr/lib64/mozilla-firefox/plugins


So why don't it work?  I got lots of time for exersizes in futility.

later 
ray

---

### Post by Frak on 2009-01-10
> **raypsi said:**
> libnpjp2.so

    File name: libnpjp2.so

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_12 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_12 	Java 		Yes
application/x-java-vm-npruntime 	Java 		Yes

Is what I gots under about:plugins

But it don't worky. I go to the test java web page and it's says it don't work.

**Help says I gots this: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.19) Gecko/20081216 Ubuntu/8.04 (hardy) Firefox/2.0.0.19**

I downloaded this from a java https page: 

**/home/ray/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin**

when I installed it, it showed up here: /home/ray/jre1.6.0_12

and I linked to **/usr/lib64/mozilla-firefox/plugins**

 using:

** sudo ln -s /home/ray/jre1.6.0_12/lib/amd64/libnpjp2.so**

In a terminal at /usr/lib64/mozilla-firefox/plugins


So why don't it work?  I got lots of time for exersizes in futility.

later 
ray
You should probably follow as above and install it to your /opt directory (best place for development stuff). Once there, just link it to your home directory firefox preferences. That way, firefox will detect the plugin from the user directory. This way, it breaks a bit less and you shouldn't have as much problems ;)

---

### Post by raypsi on 2009-01-11
Well tanks alot I couldn't get the default provider to worky it had a sytax error of sum kink. But after the firefox 64 bit updated from auto update it worked fine following ur instructions.
Although I got the java from here: **[https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)**
Which provides a 22 dec 2008 dated version I didn't notice the date difference but I got it all worked out tanks agin.

later
ray

---

### Post by ready.eddy on 2009-01-15
This is brilliant .. I have had java problems for the last six months and now they are fixed. But I had to remove my previous attempts to get this to work. In particular, after I had followed the steps in the post, I removed the old icedtea gcjwebplugin using

```
sudo apt-get remove icedtea-gcjwebplugin
```

---

### Post by Frak on 2009-01-15
> **ready.eddy said:**
> This is brilliant .. I have had java problems for the last six months and now they are fixed. But I had to remove my previous attempts to get this to work. In particular, after I had followed the steps in the post, I removed the old icedtea gcjwebplugin using

```
sudo apt-get remove icedtea-gcjwebplugin
```
Thanks, I'll add that.

---

### Post by deepclutch on 2009-01-16
thanks.it is useful.

---

### Post by InspiredIndividual on 2009-01-17
Thanks very much for the useful HOWTO. It worked like a charm for me.

---

### Post by Stinger on 2009-01-20
Thank  you very much, just the post I've been looking for.
Works like a charm !

UBUNTU ROCKS !

:guitar:

---

### Post by gaffurabi on 2009-01-20
i did all the steps in the tutorial but firefox still does not recognize java!

---

### Post by Frak on 2009-01-20
Could you give me the output of ```
ls ~/.mozilla/plugins/
``` ?

---

### Post by gaffurabi on 2009-01-20
sure:
```
varg@varg-desktop:~$ ls ~/.mozilla/plugins/
libnpjp2.so

```

---

### Post by Frak on 2009-01-20
Hmm... is firefox 32-bit by any chance? This is probably a stupid question, but might as well eliminate the easy ones first.

---

### Post by gaffurabi on 2009-01-20
```
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.5) Gecko/2008121623 Ubuntu/8.10 (intrepid) Firefox/3.0.5
```

pretty sure it is 64bit

---

### Post by Frak on 2009-01-20
Last thing I can think of is: Did you make sure to run the sudo update-alternatives part? I can't remember off the top of my head if that involves firefox or not, but it's worth a try.

---

### Post by gaffurabi on 2009-01-21
> **Frak said:**
> Last thing I can think of is: Did you make sure to run the sudo update-alternatives part? I can't remember off the top of my head if that involves firefox or not, but it's worth a try.

i did everything in tutorial step by step but ffox still doesnt recognize sun java. i guess i'll use it with other plugins that ffox offers.

---

### Post by JacenMandarin on 2009-01-21
Hey, thanks, this worked like a charm! One note though, if you're using the jdk isntead of the jre, the plugin is in a different spot. It's at 

/opt/java/jdk1.6.0_12/jre/lib/amd64/libnpjp2.so

---

### Post by xoros on 2009-01-22
What happens when it comes time to update the java plugin? 
You just do the same steps for a newer version?

These guides never seem to cover updating. :\

---

### Post by gaffurabi on 2009-01-22
well i installed xubuntu and it somehow worked on that :S

---

### Post by Frak on 2009-01-22
> **xoros said:**
> What happens when it comes time to update the java plugin? 
You just do the same steps for a newer version?

These guides never seem to cover updating. :\

Just do it again. If you want to be scrupulously clean, you could remove the old directory.

> **gaffurabi said:**
> well i installed xubuntu and it somehow worked on that :S

:o :)

---

### Post by deepclutch on 2009-01-31
for me ,it is ```
ln -s /opt/java/jre1.6.0_12/lib/amd64/libnpjp2.so                   /usr/lib/firefox-3.0.5/plugins/ 
```

and if you need a gui for update-alternatives:
**apt-get install galternatives **
--
Bye for now :)

---

### Post by Ng Oon-Ee on 2009-02-01
> **gaffurabi said:**
> i did everything in tutorial step by step but ffox still doesnt recognize sun java. i guess i'll use it with other plugins that ffox offers.
Hi, not sure if you got this solved, but for me the same thing happened, I traced it down to linking the wrong file (in nautilus my ~/.mozilla/plugins showed a broken link). Maybe you might want to check that out.

Thanks to the OP for this useful thread.

---

### Post by xaris106 on 2009-02-12
ok whoever has the broken link problem I found the solution.

You have to be in the ~/.mozilla/plugins folder and make the link from there. Don't know why but it worked.

After you have completed the instructions and you are at the link part do:
```

cd ~/.mozilla/plugins
ln -s /opt/java/jre1.6.0_*/lib/amd64/libnpjp2.so
```

Restart firefox and you are done.

Also if you still have problems check if you have given execution rights in the bin folder.

Do
```

cd /opt/java/jre1.6.0_*/bin
chmod +x *
```

I saw that at the sun site here [http://download.java.net/jdk6/]("http://download.java.net/jdk6/")

---

### Post by junnuh on 2009-02-26
Thank you Frak!

I installed also the new version jre1.6.0_14 using your HOWTO and now with the newer version also RunEscape works. The last reason why I have been using 32bit java.

When doing it to my desktop PC I didn't remove the older version and the browser plugin did not work. Also the java page didn't regocnice that I was using jre1.6.0_14.

So it's best to remove old version first and also the java-plugin link!;) I did it to my laptop just couple of minutes ago and installed the jre 1.6.0_14  and the java and the browser plugin works fine!!

This really rocks! Thanks!:guitar:

with ligth junnuh

---

### Post by deepclutch on 2009-03-01
Was trying Epiphany-webkit(from ppa repo) .to have the epiphany java plugin:
```
ln -s /opt/java/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib/epiphany-webkit/2.24/plugins/ 
```

---

### Post by Jozza The Wick on 2009-05-02
From another thread, I found that I had to run this command to remove another component of the IceTea plugin

sudo apt-get remove cacao-oj6-plugin

[http://ubuntuforums.org/showthread.php?p=7199723#post7199723](http://ubuntuforums.org/showthread.php?p=7199723#post7199723)

Maybe you could add that to the guide? Thanks so much for helping me get Java running!

---

### Post by Frak on 2009-05-03
Thanks! Added.

---

### Post by aparigraha on 2009-05-05
as deepclutch said, but with the **sudo**: ```
**sudo** ln -s /opt/java/jre1.6.0_14/lib/amd64/libnpjp2.so /usr/lib/firefox-3.0.10/plugins/
```

;)

Excellent guide!
Thx

---

### Post by greythorne on 2009-05-13
worked like a charm! 

Thanks

---

### Post by deepclutch on 2009-07-23
[COLOR=Red]_**UPDATE:**_[/COLOR]
Jre7 Experimental versions are available.
For Extracting .jar archive ,sun-java-6 jre/bin needs to be installed 

```
 /usr/lib/jvm/java-6-sun/jre/bin/java -jar  jre-7-ea-bin-b78-linux-x64-17_dec_2009.jar
```Accept the Agreement and Extract into Desktop and later copy the directory jre1.7.0 to /opt(else directly extract as root to /opt)
[http://download.java.net/jdk7/binaries/](http://download.java.net/jdk7/binaries/)
_**64-bit:**_
[http://www.java.net/download/jdk7/binaries/jre-7-ea-bin-b78-linux-x64-17_dec_2009.jar](http://www.java.net/download/jdk7/binaries/jre-7-ea-bin-b78-linux-x64-17_dec_2009.jar)

the extracted jre1.7.0 is placed at /opt directory.
```
cd /opt/jre1.7.0/bin;chmod +x * 
```Working Fine on Firefox-3.5.1 .
you have to symlink :
```
sudo ln -sf /opt/jre1.7.0/lib/amd64/libnpjp2.so /usr/lib/firefox/plugins/ 
```if that doesnot worked:
```
sudo ln -sf /opt/jre1.7.0/lib/amd64/libnpjp2.so /usr/lib/firefox-3.5.1/plugins/ 
```or
```
sudo ln -sf /opt/jre1.7.0/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins/ 
```Good Luck!

Incase ,No Java variable is defined with update-alternatives(in case no other java installed) ,Run this :
```
 **update-alternatives --install /usr/bin/java java /opt/jre1.7.0/bin/java 50**
```

---

### Post by MontelEdwards on 2009-07-23
> **Nublet said:**
> i followed the guide, however 
```
./jre-<miscellaneous version information> -amd64-<date>.bin
```
did not work, so i used
```
sudo sh ./jre-<miscellaneous version information> -amd64-<date>.bin
```
instead, and it doesn't work (java doesn't show up in firefox' addons manager, and javatester says it's disabled). did i do it wrong? regardless of wheter it's my fault or not, how can i repair it?
The reason that did not work is because the file was not marked as executable :)

---

### Post by KewlEugene on 2009-07-27
(I have Jaunty 9.04 amd64 Firefox 3.5). That procedure worked partially for me.

I am able to get Java Test to work.

[http://www.javatester.org/version.html](http://www.javatester.org/version.html)

And Java Web Start works.

[http://java.sun.com/javase/technologies/desktop/javawebstart/apps/draw.jnlp](http://java.sun.com/javase/technologies/desktop/javawebstart/apps/draw.jnlp)

But the Java Web Start on the Java F/X page gets 'Unable to Launch the Application' at:

[http://javafx.com/samples/BrickBreaker/index.html](http://javafx.com/samples/BrickBreaker/index.html) <click 'launch'>

and any of the sample Java F/X programs don't load either at:

[http://www.javafx.com/samples/ProjectManager/index.html](http://www.javafx.com/samples/ProjectManager/index.html)

However, the above two errant links work on Firefox 3.5 and IE on Win/XP.

---

### Post by perty on 2009-08-27
Same problem here. Although once in a while I discover JavaFX applets or web-starts that work.

However, the javatester does not tell you everything so run this program instead.

import java.util.Properties;


public class ListSystemProperties {

    /**
     * @param args
     * @throws Exception 
     */
    public static void main(String[] args) throws Exception {
        Properties props = System.getProperties();
        
        props.storeToXML(System.out, "Show me all properties!");
    }

}

I did use the package manager to get the sun-java6 package and got the following:
<entry key="java.endorsed.dirs">/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/endorsed</entry>
<entry key="os.arch">amd64</entry>

So it is as simple as that, use the package manager. But it doesn't help the JavaFX problem with amd64.

---

### Post by WarHawk-AVG on 2010-02-13
Perfect!

Gotta restart Firefox to take effect!

---

### Post by Pjotr123 on 2010-02-16
I've written an even more "dumbed down" how-to for 64 bit:
[http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU-9.10](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU-9.10)

Only knowledge required is how to use copy/paste. :)

---

### Post by skjones on 2010-04-12
worked like a charm, thanks.  these web forums makes linux life easier for folks like me...:)

---

