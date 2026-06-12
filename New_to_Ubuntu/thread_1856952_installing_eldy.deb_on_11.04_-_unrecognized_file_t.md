---
title: "installing eldy.deb on 11.04 - unrecognized file type?"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by spudchick on 2011-10-09
Hi,

recently installed natty narwhal on a Shuttle touch-screen all-in-one.  Ubuntu works fine but the goal was to get Eldy on it, which hopefully will make it easy for my mother-in-law to use (who has never used a computer).

So... have installed Ubuntu a couple of times but have not needed to install something not available through the software center until now.  My background is mostly Windows install/config.

First, I could only find a link to get Eldy as a tar.gz, but finally found a link to a deb file.

[www.psychocats,net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware") 

says that when opening a deb file, Firefox should automatically recognize it as a Debian package and suggest opening with the Ubuntu Software Center (default).  However, when I try to download Eldy.deb from the link here:

[http://linuxforelderly.wordpress.com/]("http://linuxforelderly.wordpress.com/")

it seems that Firefox (or Ubuntu) doesn't recognize the deb file as a Debian package--where it should say "which is a: Debian package" in the download dialog, it says "which is a: DEB file" and defaults to the Save File option; when I try to change it to Open With, I can't find "Ubuntu Software Center (default)".

I'm hoping to get the deb file to work so I can avoid the lengthier and less familiar installation instructions for the time being. Is there something I need to install on Ubuntu or in Firefox to get this download recognized as a Debian package, or is there possibly something wrong with the Eldy.deb file?

Thanks in advance, 

a perplexed 

spud

---

### Post by cavh on 2011-10-09
You can use the terminal to install a deb file. First read a bit: [http://manpages.ubuntu.com/manpages/natty/en/man1/dpkg.1.html]("http://manpages.ubuntu.com/manpages/natty/en/man1/dpkg.1.html")

Then open a terminal: Applications - Accessories - Terminal 

Now navigate to the folder containing the deb file:
```

cd <enter path here>
```

For example, if the deb file is on your desktop:

```
cd /home/<your user name here>/Desktop
```

then make the file executable:

```
chmod u+x <enter filename including the .deb extension>
```

Then enter the dpkg command:

```
dpkg -i <enter deb filename here including the .deb extension>
```

---

### Post by spudchick on 2011-10-09
Thank you cav.  I decided to try it this way:

[http://howtos.eldy.net/2009/12/01/install-eldy-on-linux/]("http://howtos.eldy.net/2009/12/01/install-eldy-on-linux/")

and was able to get it to run, but i realize there's an issue with Sun java6 jre, which Eldy requires.  

I tried installing it using 

apt-get install sun-java6-jre 

but it doesn't seem to install SUN java. After running it, it seems to still be using the open java included with Ubuntu.

```
eldy@ubuntu4eldy:/etc/apt$ java -v
Unrecognized option: -v
Could not create the Java virtual machine.
eldy@ubuntu4eldy:/etc/apt$ java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK Server VM (build 20.0-b11, mixed mode)

```


So I tried following the instructions here:

[http://www.multimediaboom.com/how-to-install-java-in-ubuntu-11-04-natty-narwhal-ppa/]("http://www.multimediaboom.com/how-to-install-java-in-ubuntu-11-04-natty-narwhal-ppa/")

[I]The best solution is to use this PPA for more further Java updates. To install Java in Ubuntu 11.04 Natty Narwhal, open a Terminal and type :

    sudo add-apt-repository ppa:ferramroberto/java
    sudo apt-get update
    sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
[/I]

But I don't think it's adding the repository line. I think I figured out that the add should have appended some lines to the sources.list file?  But when I cat the file before and after the command it doesn't seem to have added the desired information.

```
eldy@ubuntu4eldy:/etc/apt$ sudo add-apt-repository ppa:ferramroberto/java 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 3E756CF119B127D4DA40A186B725097B3ACC3965
gpg: requesting key 3ACC3965 from hkp server keyserver.ubuntu.com
gpg: key 3ACC3965: "Launchpad lffl" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
eldy@ubuntu4eldy:/etc/apt$ sudo apt-get update
Ign http://security.ubuntu.com natty-security InRelease
Ign http://extras.ubuntu.com natty InRelease                        
Ign http://ppa.launchpad.net natty InRelease                         
Hit http://security.ubuntu.com natty-security Release.gpg            
Hit http://ppa.launchpad.net natty Release.gpg                       
Hit http://extras.ubuntu.com natty Release.gpg                       
Hit http://security.ubuntu.com natty-security Release                
Hit http://ppa.launchpad.net natty Release                                     
Hit http://extras.ubuntu.com natty Release                                     
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://ppa.launchpad.net natty/main Sources                      
Hit http://extras.ubuntu.com natty/main Sources                      
Hit http://security.ubuntu.com natty-security/restricted Sources     
Hit http://security.ubuntu.com natty-security/universe Sources       
Hit http://security.ubuntu.com natty-security/multiverse Sources     
Hit http://security.ubuntu.com natty-security/main i386 Packages     
Hit http://security.ubuntu.com natty-security/restricted i386 Packages
Hit http://ppa.launchpad.net natty/main i386 Packages                
Ign http://ppa.launchpad.net natty/main TranslationIndex             
Hit http://extras.ubuntu.com natty/main i386 Packages                
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex  
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://extras.ubuntu.com natty/main Translation-en_US            
Ign http://extras.ubuntu.com natty/main Translation-en               
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Ign http://security.ubuntu.com natty-security/universe Translation-en
Hit http://us.archive.ubuntu.com natty Release.gpg
Hit http://us.archive.ubuntu.com natty-updates Release.gpg
Hit http://us.archive.ubuntu.com natty Release
Hit http://us.archive.ubuntu.com natty-updates Release
Hit http://us.archive.ubuntu.com natty/main Sources
Hit http://us.archive.ubuntu.com natty/restricted Sources
Hit http://us.archive.ubuntu.com natty/universe Sources
Hit http://us.archive.ubuntu.com natty/multiverse Sources
Hit http://us.archive.ubuntu.com natty/main i386 Packages
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/universe i386 Packages
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-updates/main Sources
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources
Hit http://us.archive.ubuntu.com natty-updates/universe Sources
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Reading package lists... Done
eldy@ubuntu4eldy:/etc/apt$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-fonts is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
The following package was automatically installed and is no longer required:
  linux-headers-2.6.38-8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
eldy@ubuntu4eldy:/etc/apt$ java -v
Unrecognized option: -v
Could not create the Java virtual machine.
eldy@ubuntu4eldy:/etc/apt$ java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK Server VM (build 20.0-b11, mixed mode)
eldy@ubuntu4eldy:/etc/apt$ 

```


And still, same results as before:  can't use java -v, and java -version shows it using the open jdk.

Eldy will run but Eldy's mail and web won't work because it depends on Sun java running browser applications (I guess..?). 

I think this is a different question now, more about forcing Sun java as the default.  But all help is appreciated.

---

### Post by cavh on 2011-10-09
To set Sun Java as default, see the part in the following link which contains the command

```
sudo update-alternatives --config java
```

Link: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

To install Sun Java (if your initial install wasn't successful), suggest going the 'recommended' route and not using a PPA: see the above link.

---

### Post by spudchick on 2011-10-09
Thanks for hanging in there with me, cavh.  

I got it to where Sun java seemed to be the default but could not get it to show as a plugin option in Firefox.  By the time I got there, I had dome something to screw up the wireless (kept dropping out and restarting) and also the touchscreen, without which this is kind of pointless.

I ended up reinstalling Ubuntu from scratch.  Haven't resumed trying to get Sun java on yet, just downloaded Eldy again to capture the error message I get when trying to run browser features in Eldy.  Don't know if it will make any sense. It is exacty the same now as it was after I had gotten Sun java set up before.  It's got to have to do with the browser but just don't know what to do here.

Feel like I'm going in circles now and starting to lose it a little.

---

### Post by spudchick on 2011-10-09
Failed to create chrriis.dj.nativeswing.swtimpl.components.NativeWebBrowser[1,22387624]

Reason: 
	java.lang.RuntimeException: java.lang.reflect.InvocationTargetException
	java.lang.reflect.InvocationTargetException
	org.eclipse.swt.SWTError: No more handles [Unknown Mozilla path (MOZILLA_FIVE_HOME not set)]

---

### Post by cavh on 2011-10-10
Sorry, I have no more ideas on this, perhaps the Eldy forums are a better bet.

Maybe just ask your mother-in-law to try Ubuntu as is, i.e. forget Eldy? She might surprise you :P

---

### Post by spudchick on 2011-10-10
> **cavh said:**
> Sorry, I have no more ideas on this, perhaps the Eldy forums are a better bet.

Yes, I submitted a question to them last night (though there isn't really a level of Eldy user support in between basic help videos posted online and then submitting a question directly to the developer's group).  

I did notice searching around that there are lots of little apps floating around that often have this same error, but the resolutions were over my head and appeared to involve changing settings in the apps, not Ubuntu/Firefox settings.  Having developed small Windows apps, I think it's similar to a problem I've seen when I add a browser control to one of my db interfaces and the expected version of IE isn't present on the system. 

> Maybe just ask your mother-in-law to try Ubuntu as is, i.e. forget Eldy? She might surprise you :P

Well, it crossed my mind last night! She's not a dummy, mind you, but very panicky and technology-skittish. Have seen her panic when confronted with an "answering machine" instead of a live person. 

She was thinking of getting one of those SimplicITy computers for the elderly but it looked like a ripoff, overpriced for the hardware specs and more features than she needed.  Had read about Eldy--free-- and figured I could put something together for her without having to pay for a Windows license that wouldn't even get used.

In working with natty (which is quite nice, hadn't played with Ubuntu in over two years) and seeing how Eldy promises to work, I feel she has a fair chance of dealing with Eldy successfully, but not Ubuntu.  For one, her hands are not so good anymore, and the big simple buttons in Eldy work so well with the touchscreen, she'll rarely have to use the mouse, if ever.

Anyway, thanks for your suggestions, cavh.  If I can get this working I'll post on the resolutions. 

spud

---

