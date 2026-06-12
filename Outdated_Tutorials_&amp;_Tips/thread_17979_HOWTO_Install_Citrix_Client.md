---
title: "HOWTO: Install Citrix Client"
date: 2005-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by rsay on 2005-03-03
I was trying to get citrix installed to connect with my office and it is working, but I sort of patched together the idea from several different places that I found with google. I thought if I put down what I did I might save somebody some time and maybe somebody smart could tell me why this worked. BTW, I use firefox as a browser.

1. I went to citrix.com and downloaded the linux client version 8.0

2. I untarred it in my home directory (right click, extract here)

3. sudo apt-get install libxaw6        # not sure if this was necessary

4. sudo apt-get install mozilla         # this was definitely necessary

5. cd linuxx86.tar.gz_FILES              # the directory created in #2

6. sudo ./setupwfc                            # follow onscreen instruction to install

7. close firefox if it was open, re-open and connect to citrix server  


I hope this will be a helpful starting point.

---

### Post by rsay on 2005-03-08
I tried setting this up on another system and the plugin didn't show up in firefox. I manually applied the link and all was well.

ln -s /usr/lib/ICAClient/npica.so /usr/lib/mozilla-firefox/plugins/npica.so

---

### Post by draconas on 2005-03-23
Okay. I did the top part. I can get the login page for my company's NFusion site. I log in, the published apps appear. When I click on one of the links, a smaller Citrix client window pops up, then disappears followed by nothing else. I tried running the link command in the reply but get the following error:

ln: when making multiple links, last argument must be a directory

Any thoughts?

---

### Post by rsay on 2005-04-08
For me, the battle was won once the small citrix client window popped up. There must be something different about their server. You might find out from your admins what version of the client you need for your company. I would also google the error message and see if there is any info out there on it.

---

### Post by bgrant75 on 2005-04-09
In relation to connecting to a citrix server please note that when you access the citrix server using Ubuntu you will get a temp licence. YOU MUST alert your Net Admin so he can make the necessary arrangements for you to have a payed for licence.

Remember you are connecting to a M$ server and hence you will need to pay the toll for a terminal server Cal.

The temp licence work for 60 day default and may vary...ask you Net Admin.

I only know this cause I have been using Hoary for the last 2 months solid in my M$ enviroment and travell and got caught out with no access.

BG

---

### Post by draxula on 2005-04-14
Hi,

I got Citrix 8.x working in Hoary Preview, but now when I run wfcmr I get the following error:

stephan@stephan-x64:~$ /usr/lib/ICAClient/wfcmgr
Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to type compound text string
Segmentation fault


Any ideas?
Might be something stupid :???: 

Stephan

---

### Post by joplass on 2005-05-13
Guys,
Please I need help.  I install citrix fine but I can't connect to my company server.  Is there a trick here?  Or can someone please walk me through the configuration process?  
Thanks,

---

### Post by lostrone on 2005-06-15
Hi rsay,

first of all: thanks very much for your useful howto.

In my case, I had to do the modification, instead
4. sudo apt-get install mozilla 
I had to 
4. sudo apt-get install mozilla-firefox

But in addition to that, I encountered the problem when starting the Citrix "You have not chosen to trust xyz, the issuer of the server's security certificate".
Firefox HAS this certificate already built in, so that it took a while to find the problems base and solution under the following link:
"http://www.thedance.net/~roth/CAC/citrixlinux/"
It describes, that the certificate has to be stored also and explecitely under /usr/lib/ICAClient/keystore/cacerts

After this final step of copying the specific .crt file into this location, everything works fine. 

Thanks and
Best regards,
L.

---

### Post by bognare on 2005-07-01
hi,

 I am now in this forum, and this is my first reply. :-)

 when i want to start setupwfc i get an error: 

-----------------------------------------------------------------------------------------------------
[email]bognare@Joey:~/Citrix/linuxx86/linuxx86.cor[/email]$ ./setupwfc
cat: /home/bognare/Citrix/linuxx86/linuxx86.cor/./pkginf/V*: No such file or directory

This installation is not the correct type for a Linux (x86) workstation.
-------------------------------------------------------------------------------------------------------

 Can somebody help me, what is the problem. I have ubuntu hoary.

---

### Post by quozl on 2005-08-11
[QUOTE=bognare] when i want to start setupwfc i get an error: 

-----------------------------------------------------------------------------------------------------
[email]bognare@Joey:~/Citrix/linuxx86/linuxx86.cor[/email]$ ./setupwfc
cat: /home/bognare/Citrix/linuxx86/linuxx86.cor/./pkginf/V*: No such file or directory

This installation is not the correct type for a Linux (x86) workstation.
-------------------------------------------------------------------------------------------------------

 Can somebody help me, what is the problem. I have ubuntu hoary.[/QUOTE]

I'm getting the same error.

---

### Post by shadow07 on 2005-09-19
I too get the same error as above ("This installation is not the correct type for a Linux (x86) workstation.")

Any ideas?  I have installed libmotif3 and libxaw6.

---

### Post by markbrazil on 2005-10-30
[QUOTE=rsay]I was trying to get citrix installed to connect with my office and it is working, but I sort of patched together the idea from several different places that I found with google. I thought if I put down what I did I might save somebody some time and maybe somebody smart could tell me why this worked. BTW, I use firefox as a browser.

1. I went to citrix.com and downloaded the linux client version 8.0

2. I untarred it in my home directory (right click, extract here)

3. sudo apt-get install libxaw6        # not sure if this was necessary

4. sudo apt-get install mozilla         # this was definitely necessary

5. cd linuxx86.tar.gz_FILES              # the directory created in #2

6. sudo ./setupwfc                            # follow onscreen instruction to install

7. close firefox if it was open, re-open and connect to citrix server  

8. Create run script pnagent,  setting LD_LIBRARY_PATH=/usr/X11R6/lib before running wfcmgr

---

### Post by markbrazil on 2005-10-31
[QUOTE=markbrazil][QUOTE=rsay]I was trying to get citrix installed to connect with my office and it is working, but I sort of patched together the idea from several different places that I found with google. I thought if I put down what I did I might save somebody some time and maybe somebody smart could tell me why this worked. BTW, I use firefox as a browser.

1. I went to citrix.com and downloaded the linux client version 8.0

2. I untarred it in my home directory (right click, extract here)

3. sudo apt-get install libxaw6        # not sure if this was necessary
3a. sudo apt-get install libmotif3
4. sudo apt-get install mozilla         # this was definitely necessary

5. cd linuxx86.tar.gz_FILES              # the directory created in #2

6. sudo ./setupwfc                            # follow onscreen instruction to install

7. close firefox if it was open, re-open and connect to citrix server  

8. Create run script pnagent,  setting LD_LIBRARY_PATH=/usr/X11R6/lib before running wfcmgr, also add ICAClient to front of path in script   [/QUOTE]
9. change permissions on *.DLL to give rwx  (Had problems trying to access PDCRYPT1.DLL!)

---

### Post by esisa on 2005-10-31
[QUOTE=shadow07]I too get the same error as above ("This installation is not the correct type for a Linux (x86) workstation.")

Any ideas?  I have installed libmotif3 and libxaw6.[/QUOTE]

I get the same message. Seems like some are referring to Citrix IcaClient version 8 as opposed to version 9 that I download. Has this software been recently updated? Is is possible to get version 8 instead?

---

### Post by neurator on 2005-11-01
[QUOTE=markbrazil][QUOTE=markbrazil]
9. change permissions on *.DLL to give rwx  (Had problems trying to access PDCRYPT1.DLL!)[/QUOTE]


I'm not sure how to go about writing this script that you created.  What is the text in the script?

---

### Post by waratah on 2006-05-08
I could not find the certificate files on the thawte site after a bit of googling...

Download ThawteRoot.crt from [http://www2.slac.stanford.edu/computing/windows/services/citrix/linux_client.htm](http://www2.slac.stanford.edu/computing/windows/services/citrix/linux_client.htm) and place it under /usr/lib/ICAClient/keystore/cacerts.

---

### Post by ssavelan on 2007-01-15
The instructions found on this present page did not quite work for me.

If anyone else is caught, [these instructions]("http://bin-false.org/?p=13") worked for me.

in about 1 minute...

---

### Post by bkj1 on 2007-02-03
for those getting this error:
----------------------------------------------------------------------------------------------------
[email]bognare@Joey:~/Citrix/linuxx86/linuxx86.cor[/email]$ ./setupwfc
cat: /home/bognare/Citrix/linuxx86/linuxx86.cor/./pkginf/V*: No such file or directory

This installation is not the correct type for a Linux (x86) workstation.
-------------------------------------------------------------------------------------------------------

the solution is simple.

You had run the installation script from the wrong location.
Change to your homedir, run ./setupwfc

linuxx86/linuxx86.cor/setupwfc is wrong!

Reason: Installation script & pkginf are located in the tar's root.
Create a subfolder in your homedir. Copy the tar to that subfolder. Extract the tar. Run setupwfc from that subfolder.

Hope that helped...

---

### Post by octoberdan on 2007-06-03
The archive no longer has setupwfc in it! Instead a help script is there telling you to get it off the CD (which I don't have a copy of). Can anyone hook me up with a link of where I can get my hands on the setupwfc? Or send me an older version of the archive that is still 10?

EDIT: Doh! I'm an idiot. I expected the setupwfc to be in the directory that was decompressed, not outside of it. Found it! Thanks anyways.

---

### Post by engineering.concepts on 2007-06-03
I tried a few variations but have not gotten Citrix to work.
This is my error:

com.citrix.certicom.b.b.a.b: Bad certificate beginning
	at com.certicom.b.a.a.a.u.a(u.java)
	at com.certicom.b.a.a.a.u.<init>(u.java)
	at com.certicom.b.a.a.a.v.<init>(v.java)
	at com.citrix.certicom.b.b.a.g.a(g.java)
	at com.citrix.certicom.b.b.a.g.a(g.java)
	at com.citrix.sdk.security.ssl.ConnectionModel.addCACertificate(ConnectionModel.java)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.citrix.client.io.net.ip.n.h(Unknown Source)
	at com.citrix.client.io.net.ip.x.b(Unknown Source)
	at com.citrix.client.io.net.ip.x.c(Unknown Source)
	at com.citrix.client.io.net.ip.x.a(Unknown Source)
	at com.citrix.client.io.net.ip.x.connect(Unknown Source)
	at com.citrix.client.io.net.ip.v.<init>(Unknown Source)
	at com.citrix.client.io.net.ip.v.<init>(Unknown Source)
	at com.citrix.client.module.td.tcp.TCPTransportDriver.q(Unknown Source)
	at com.citrix.client.module.td.TransportDriver.run(Unknown Source)

any thoughts?
Thanks for your assistance.

---

### Post by iqag1060 on 2007-06-10
You're better off downloading the rpm rather than the tar from the [Citrix download page]("http://citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186#top"). Then use alien to convert it to a deb. Very straightforward, and much more reliable than the installation script in the tar. The details are in the [Community Docs]("https://help.ubuntu.com/community/CitrixICAClientHowTo").

---

### Post by gigahz on 2007-08-03
I had to manually find libXaw.so.6 and put it into /usr/lib. Then I got the mentioned problem:

**Citrix ICA client reports “Proxy connection failed” when connecting**

This is **caused by Citrix expecting all linux users to use netscape**. Since I don't... 

After some looking, I found [http://ccgi.maxpower.plus.com/category/technology/thin-client/citrix/](http://ccgi.maxpower.plus.com/category/technology/thin-client/citrix/) solving my problem.

Here's some code, copy-and-paste to a terminal and you're green (well, I was anyway):

```
cd
mkdir .netscape
cd .netscape
echo "user_pref("network.proxy.http","");" > preferences.js
echo "user_pref("network.proxy.http_port", 80);" >>preferences.js
echo "user_pref("network.proxy.type", 0);" >>preferences.js

```

---

### Post by gerard.volker on 2007-08-17
:confused:
I have the ICA 10 client running fine on Feisty--almost!

After the client launches (through Firefox or PNAgent--I get the same result0, when I authenticate and connect to my server (which happens successfully and very quickly), the client hangs on "Sending module options to server".  After a couple of minutes i get a timeout/reconnect box and a separate remote SSL terminated box.  

I've installed and re-installed, re-configured, and can't get past this point after several hours of troubleshooting.  Any ideas would be most excellent.

Thanks in advance.

-Gerard

---

### Post by Yes on 2007-09-05
When ever I try to use any of my applications in Citrix, I get the error "You have chose not to  trust Equifax Secure Certificate Authority, the issuer of the server's security certificate."  Is there any way to fix this?

Thanks.

---

### Post by CourteousCucumber on 2007-12-15
I was getting the same "You have chosen not to trust Equifax...blah....blah".

Here is how I have got it working.  I roughly followed in installation instructions at:

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

and then installed the certificate file from:

[http://www.geotrust.com/resources/root_certificates/index.asp#WireLineandWireless](http://www.geotrust.com/resources/root_certificates/index.asp#WireLineandWireless)

1. Download "Equifax Secure Certificate Authority" file
2. Rename to blah...blah.crt
3. Copy .crt file into /usr/lib/ICACleint/keystore/cacerts

I'm a NOOB so let me know if you need more details.

Greg

---

### Post by ivago on 2007-12-26
any change of an ica client getting into a gutsy repo soon?

---

### Post by compuwalah on 2008-10-20
On Hardy (8.04) I followed following steps and it worked fine.

Installation : Hardy + all updates
1) Installed libmotif3  (from synaptic package manager)
2) Unzipped the version 10 Citric CLient (en.linuxx86.tar.gz) in a subdirectory. Ran the setupwfc with my login ID (there is no need to run the setupwfc with sudo) and accepted all defaults. I also answered yes for integration with kde/gnome. 
3) Then opened  .bashrc file of my home dir (I am using bash so adjust according to your shell) and added following lines to it

export ICAROOT=${HOME}/ICAClient/linuxx86

4) Copied ThwateRoot.crt to
      /home/cwalah/ICAClient/linuxx86/keystore/cacerts
         (replace cwalah with your login ID) 
    (see initial posts of this mail as where ot get ThawteRoot.crt)
    and made permission on it chmod 444 ThawteRoot.crt

5) Closed firefox. Opened a xterm (or terminal).
   Verified that ICAROOT is set (env | grep ICAROOT) to 
   /home/cwalah/ICAClient/linuxx86
      (in your will see your login id instead of cwalah) )

6) Ran firefox from same termimal.


So when I login to my company site everything working fine. There are lot of error thrown on xterm/terminal window (from which firefox was launched) like

 Locking assertion failure.  Backtrace:
    and lots stack dumps.

But in spite of those everything is working fine.

---

### Post by emademal on 2009-03-29
I was trying  install  citrix to connect with my office and it does not work, how can i do that

---

### Post by Procuro on 2009-05-24
Since this howto is 4 years old and it was the first citrix howto I ran into, this might make it easier for people.

Get Citrix version 11 (or latest version) here: [http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1](http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1)  (download link may change when new version comes out)

Extract it and run setupwfc in the terminal and install it (just keep default path in home folder so you can write to it easily.)

Navigate to usr/share/ca-certificates/mozilla

Copy all the files in there to your citrix certificates to your citrix client. The default install is located in your home folder in ICAclient/linuxx86/keystore/cacerts and paste all the certificates from the mozilla folder to this folder. This should fix any certificate errors.

After that lauch firefox and login and you everything should hopefully work great. Hope this helps :popcorn:

---

### Post by aramiz on 2009-07-29
> **waratah said:**
> I could not find the certificate files on the thawte site after a bit of googling...

Download ThawteRoot.crt from [http://www2.slac.stanford.edu/computing/windows/services/citrix/linux_client.htm](http://www2.slac.stanford.edu/computing/windows/services/citrix/linux_client.htm) and place it under /usr/lib/ICAClient/keystore/cacerts.

This worked very well for me. Thanks a lot!

---

### Post by dspisak on 2009-07-31
I had no problems with Citrix and Intrepid.  I upgreaded to Citrix 11 shortly after I upgraded to Jaunty.  Now, when I go my company's site (NetGIL) Citrix will run OK for 11 to 20 minutes then the NetGIL desktop freezes.  I then have to disconnect and reconnect.  Previously I could be online for hours.

I can't find any solution.  The company's IT support folks also can't find a solution.

Has anyone had a similar desktop freeze problem?  The other application are not affected, just the NetGIL desktop.

TIA

---

### Post by Huss on 2009-11-13
> **bkj1 said:**
> 

the solution is simple.

You had run the installation script from the wrong location.
Change to your homedir, run ./setupwfc

linuxx86/linuxx86.cor/setupwfc is wrong!



Thank you!

Great help

---

### Post by Justin2860 on 2010-02-27
I tried this and this is what I do (in a terminal)

justin@justin:~$ sudo apt-get install libxaw6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxaw6 is already the newest version.
The following packages were automatically installed and are no longer required:
  libnm-util0 dhcdbd libisc32
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
justin@justin:~$ sudo apt-get install mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla: Depends: seamonkey but it is not going to be installed
E: Broken packages
justin@justin:~$ cd linuxx86.tar.gz_FILES
bash: cd: linuxx86.tar.gz_FILES: No such file or directory
justin@justin:~$ sudo ./setupwfc
sudo: ./setupwfc: command not found
justin@justin:~$ 

It doesn't work...
is there any way
you can help....
Thanks

---

### Post by MrCheese on 2010-03-25
mouse pointer is in wrong place but only in Outlook 2007 - everything else works fine. Actual mouse pointer hot spot seems to be slightly above the top of the cursor. Anybody else got this issue? 

Paul.

---

### Post by AlwaysTired on 2010-11-03
> **MrCheese said:**
> mouse pointer is in wrong place but only in Outlook 2007 - everything else works fine. Actual mouse pointer hot spot seems to be slightly above the top of the cursor. Anybody else got this issue? 

Paul.

Me too: when I run Matlab via citrix I get the same problem. When I tried running Word 2007 and Mathematica the problem didn't show up.

Update: Somehow the problem disappeared. I suspect it has something to do with GNOME upper pannel: when I unmaximized the window, everything was fine. Now also when the window is maximized there is no problem. I hope.

---

### Post by Trandre on 2010-12-05
Thanks I have had trouble doing this. But following your description helped:p

---

