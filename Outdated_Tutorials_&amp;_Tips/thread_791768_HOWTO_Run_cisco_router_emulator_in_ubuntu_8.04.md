---
title: "HOWTO: Run cisco router emulator in ubuntu 8.04"
date: 2008-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by hariprs on 2008-05-12
**Tested with Ubuntu Hardy**

[SIZE="3"]**Dynamips:**[/SIZE]
Dynamips is a Cisco router emulator written by Christophe Fillot. It emulates 1700, 2600, 3600, 3700, and 7200 hardware platforms, and runs standard IOS images. ( This discription is taken from [http://dynagen.org/tutorial.htm#_Toc193247991](http://dynagen.org/tutorial.htm#_Toc193247991) )

[SIZE="3"]**Dynagen:**[/SIZE]
Dynagen is a front-end for use with the Dynamips Cisco router emulator. It uses an INI-like configuration file to provision Dynamips emulator networks. It takes care of specifying the right port adapters, generating and matching up those pesky NIO descriptors, specifying bridges, frame-relay, ATM switches, etc. It also provides a management CLI for listing devices, suspending and reloading instances, determining and managing idle-pc values, performing packet captures, etc. ( This discription is taken from [http://dynagen.org/](http://dynagen.org/) )

This tutorial helps you to run cisco IOS images using Dynamips-Dynagen emulators in ubuntu. Will be much useful to those whose are preparing for cisco certifications.

This tutorial doesnot explains extended network configuration of Dynamips. This guide simply provides you on howto install Dynamips-Dynagen in ubuntu and run a cisco router IOS image in ubuntu.

Following softwares/libs are required to run Dynamips-Dynagen

1) libpcap v0.9.x
2) python v2.5.x

Use synaptic package manager to install the above softwares

1) Go to Start>System>Administration>synaptic package manager
2) Search libpcap & python
3) Mark the above mentioned versions and press apply to install.

[SIZE="3"]**Install Dynamips & Dynagen:**[/SIZE]

1) Create a new directory for dynamips

```
sudo mkdir /opt/dynamips
```

2) Change to dynamips directory

```
cd /opt/dynamips
```

3) Download latest dynagen software using wget

```
sudo wget http://downloads.sourceforge.net/dyna-gen/dynagen-0.11.0.tar.gz?modtime=1208688475&big_mirror=0
```

4) Extract the tarball

```
sudo tar -xvzf dynagen-0.11.0.tar.gz
```

5) Change to /opt/dynamips/dynagen-x.x.x directory

```
cd /opt/dynamips/dynagen-0.11.0
```

6) Look at the README.txt file to see which version of Dynamips is required for this version of Dynagen

```
less README.txt
```

At the time of this tutorial, at least dynamips version 0.2.8-RC1 is required.

7) Change to /opt/dynamips directory

```
cd /opt/dynamips
```

8 ) Download Dynamips from Dynamips blog

```
sudo wget http://www.ipflow.utc.fr/dynamips/dynamips-0.2.8-RC2-amd64.bin
```

Since my arch is AMD64bit i downloaded 64bit version, You can visit [http://www.ipflow.utc.fr/blog/](http://www.ipflow.utc.fr/blog/) to download latest and for different arch versions.

9) Use chmod to change permission

```
sudo chmod 755 dynamips-0.2.8-RC2-amd64.bin
```

10) Navigate to /usr/bin to create symbolic links for dynagen & dynamips

```
cd /usr/bin
```

```
sudo ln -s /opt/dynamips/dynamips-0.2.8-RC2-amd64.bin dynamips
```

```
sudo ln -s /opt/dynamips/dynagen-0.11.0/dynagen dynagen
```

11) Updatedb

```
sudo updatedb
```

12) Create a directory for cisco routers images

```
sudo mkdir /opt/dynamips/images
```

**[SIZE="3"]Run the simulator:[/SIZE]**

1) Download the cisco router IOS images from [www.cisco.com](www.cisco.com)
**Note:** You must have cisco login to download the IOS image. Normally cisco customer & CCIE will have a login.

2) Put the downloaded cisco IOS image in /opt/dynamips/images folder.

```
sudo mv c7200-jk9o3s-mz.123.12e.bin /opt/dynamips/images
```

3) Update the configuration file with correct image path and RAM size required. The dynagen comes with some sample configuration file. I used it for this tutorial.

```
sudo vi /opt/dynamips/dynagen-0.11.0/sample_labs/simple1/simple1.net

# Simple lab



[localhost]



    [[7200]]

    # image = \Program Files\Dynamips\images\c7200-jk9o3s-mz.124-7a.image [COLOR="Red"]<<--Comment out this windows path[/COLOR] 

    # On Linux / Unix use forward slashes:

    image = /opt/dynamips/images/c7200-jk9o3s-mz.124-7a.bin [COLOR="Red"]<<-- Uncomment and update this line with correct path
[/COLOR]
    npe = npe-400

    ram = 160 [COLOR="Red"]<<-- Update this value with required RAM size[/COLOR]

        

    [[ROUTER R1]]

    s1/0 = R2 s1/0

    

    [[router R2]]

    # No need to specify an adapter here, it is taken care of

    # by the interface specification under Router R1


```

Finally save and exit. You can also specify more configuration details in this file if you know more about dynagen config parameters.

4) Start the dynamips process

```
sudo dynamips -H 7200 &
```

5) Use the dynagen command to process the .net configuration file and start the virtual network.

```
sudo dynagen simple1.net
```

You will placed inside the dynagen console

6) Use list command to list the network equipments and port details for console access.

```
=>list
Name    Type     State     Server           Console
R1      7200     Running   localhost:7200   2001
R2      7200     Running   localhost:7200   2002
```

7) Finally telnet to the router console

```
=> telnet R1
```

**Note:** You can also use utilities like putty to telnet to router console.

To learn more about Dynamips/Dynagen visit the below links

```
http://dynagen.org/tutorial.htm#_Toc193247991
http://www.ipflow.utc.fr/index.php/Cisco_7200_Simulator
http://www.ipflow.utc.fr/blog/
```

---

### Post by MrFSL on 2008-05-13
If you are serious about cisco emulation I STRONGLY suggest GNS3.

Works great in linux. I have used this in conjunction with vmware to make a complete virtual network testbed.


[http://www.gns3.net/](http://www.gns3.net/)

---

### Post by hariprs on 2008-05-15
> **MrFSL said:**
> If you are serious about cisco emulation I STRONGLY suggest GNS3.

Works great in linux. I have used this in conjunction with vmware to make a complete virtual network testbed.


[http://www.gns3.net/](http://www.gns3.net/)

Thanks a lot, I was looking for a GUI for dynamips-Dynagen. It works for me in Hardy.

---

### Post by mizu12 on 2008-05-17
> **MrFSL said:**
> If you are serious about cisco emulation I STRONGLY suggest GNS3.

Works great in linux. I have used this in conjunction with vmware to make a complete virtual network testbed.


[http://www.gns3.net/](http://www.gns3.net/)

I installed it through Synaptic on Hardy (followed the instructions on their site), it's easy to do and it works as it has to. I tried it under windows it's painfully slow compared to Linux.

GNS3 is a great frontend to dynamips, you dont have to bother about the config files, you do all the nasty things with the GUI.

---

### Post by m83 on 2008-05-17
I find that using CISCO's PacketTracer with WINE is fulfilling all my needs for network simulation with CISCO equipment.

Setting up a Dynamips-Dynagen environment looks like a lot of trouble that is not worth the effort.

---

### Post by nickert0n on 2008-05-20
Thank you for this!

---

### Post by cormic on 2008-05-27
Just got a great little lab running in about an hour using GNS3 and the frame relay tutorial located at [http://www.blindhog.net/gns3-how-to-build-a-frame-relay-lab/](http://www.blindhog.net/gns3-how-to-build-a-frame-relay-lab/)

This is really nice piece of software.  The CPU is running at 100% but that is to be expected.

Thanks for the pointers all :)

---

### Post by geezerone on 2008-06-28
I have tried this but get the "locked R1 error"

---

### Post by hariprs on 2008-06-29
> **geezerone said:**
> I have tried this but get the "locked R1 error"

Probably you didn't configured the correct path to the image. check your configuration.

---

### Post by geezerone on 2008-06-30
Hi

Sorted it out. It was due to file permissions being that of root. Changed with ```
chown <userid> <file/directory>
``` to 'my user' and worked. Needed to remove the configuration files for the lab which had root as owner too. Once restarted the lab had files with my user permissions.

Hope this helps someone.

Regarding Synaptic - why aren't the files created in /opt/ like your and other (blindhog) tutorials?

---

### Post by tigerplug on 2008-08-26
Thankyou for the post but I'm not able to get this working on my Ubuntu Hardy 64bit setup.

Any suggestions?
Is there a different install method for x64?

I could really do with getting this working for my CCNA so any help would be really appreciated.

---

### Post by hariprs on 2008-08-26
> **tigerplug said:**
> Thankyou for the post but I'm not able to get this working on my Ubuntu Hardy 64bit setup.

Any suggestions?
Is there a different install method for x64?

I could really do with getting this working for my CCNA so any help would be really appreciated.

All the configurations given in this howto is done in Hardy 64bit. It should work without any problem, reply with your exact problem.

---

### Post by hariprs on 2008-08-26
> **tigerplug said:**
> Thankyou for the post but I'm not able to get this working on my Ubuntu Hardy 64bit setup.

Any suggestions?
Is there a different install method for x64?

I could really do with getting this working for my CCNA so any help would be really appreciated.

Customized live CD for Dyangen/Dynamips with GNS3 is available in the link. You can also try this.
[http://www.gns3-labs.com/2008/06/23/dynaslax-dynaslaxgns3-and-dynaslaxusb-livecds/](http://www.gns3-labs.com/2008/06/23/dynaslax-dynaslaxgns3-and-dynaslaxusb-livecds/)

---

### Post by cxcal on 2008-12-02
Getting this error when I execute the dynagen lab1a.net

This works on windows.  Not sure what is missing on the linux side for this.


Any advice??


*** Warning:  Connecting R7 f3/1 to R8 f3/1 resulted in:
        attempt to connect to non-existent interface in slot 3 on device R7
*** Warning:  Connecting R7 f3/2 to R8 f3/2 resulted in:
        attempt to connect to non-existent interface in slot 3 on device R7
*** Warning:  Connecting R7 f3/3 to R8 f3/3 resulted in:
        attempt to connect to non-existent interface in slot 3 on device R7
*** Warning:  Connecting F1 1:109 to 9:901 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 2:209 to 9:902 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 3:309 to 9:903 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 4:409 to 9:904 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 5:509 to 9:905 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 6:609 to 9:906 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 7:709 to 9:907 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 8:809 to 9:908 resulted in:
        switchport 9 is not connected to anything

*** Error:  errors during loading of the topology file, please correct them

---

### Post by hariprs on 2008-12-02
> **cxcal said:**
> Getting this error when I execute the dynagen lab1a.net

This works on windows.  Not sure what is missing on the linux side for this.


Any advice??


*** Warning:  Connecting R7 f3/1 to R8 f3/1 resulted in:
        attempt to connect to non-existent interface in slot 3 on device R7
*** Warning:  Connecting R7 f3/2 to R8 f3/2 resulted in:
        attempt to connect to non-existent interface in slot 3 on device R7
*** Warning:  Connecting R7 f3/3 to R8 f3/3 resulted in:
        attempt to connect to non-existent interface in slot 3 on device R7
*** Warning:  Connecting F1 1:109 to 9:901 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 2:209 to 9:902 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 3:309 to 9:903 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 4:409 to 9:904 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 5:509 to 9:905 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 6:609 to 9:906 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 7:709 to 9:907 resulted in:
        switchport 9 is not connected to anything
*** Warning:  Connecting F1 8:809 to 9:908 resulted in:
        switchport 9 is not connected to anything

*** Error:  errors during loading of the topology file, please correct them


Are you using GNS3 along with dynamips/dynagen? If not then give a try, [http://www.gns3.net/](http://www.gns3.net/)

---

### Post by cxcal on 2008-12-03
No I have not installed this tool.. Is it required?  Don't have it installed on windows.  But I'm not a linux expert so let me know if this is required.

---

### Post by cxcal on 2008-12-03
Actually I located the simple1.net file and loaded it with no problem. So let me troubleshoot my previously working .net files used in windows to see what I can find.

---

### Post by hariprs on 2008-12-03
> **cxcal said:**
> Actually I located the simple1.net file and loaded it with no problem. So let me troubleshoot my previously working .net files used in windows to see what I can find.

GNS3 is GUI frontend for Dynagen/Dynamips. It is really good. And these packages are recently included in Medibuntu repository. So you can easily install all the packages

---

### Post by akelsall on 2009-01-03
Great post hariprs!! Thanks a million!!! I followed your directions and they are "spot on." I'm running Intrepid 8.10 and it works perfect. Your tutorial beats the Hell out of what's posted on the dynagen website. 

I tried using their RPM file, and also tried just installing dyngen via "sudo aptitude install dynagen" and was getting nowhere. 

Dynamips is a great program. I had used it in Windows. Glad to see it's working in Linux. Think I'll check out the GUI front-end now (gns3).

Andy

*******************************************************************************************************
Update: GNS3 is amazing. If you want ease of use when running dynamips, use the GUI overlay known as GNS3. You will never go back to the old way!!

Wish I could design programs like this, but don't have the patience. Glad someone else does lol.
**********************************************************************************************************

---

### Post by hariprs on 2009-01-03
> **akelsall said:**
> Great post hariprs!! Thanks a million!!! I followed your directions and they are "spot on." I'm running Intrepid 8.10 and it works perfect. Your tutorial beats the Hell out of what's posted on the dynagen website. 

I tried using their RPM file, and also tried just installing dyngen via "sudo aptitude install dynagen" and was getting nowhere. 

Dynamips is a great program. I had used it in Windows. Glad to see it's working in Linux. Think I'll check out the GUI front-end now (gns3).

Andy

*******************************************************************************************************
Update: GNS3 is amazing. If you want ease of use when running dynamips, use the GUI overlay known as GNS3. You will never go back to the old way!!

Wish I could design programs like this, but don't have the patience. Glad someone else does lol.
**********************************************************************************************************


Hi Akelsall,

Thanks, Now it became even much more easier, the GNS3, dynamips/dynagen are included in the medibutu repository. You can simply enable the repository and install it very easily.

Regards
Hariprs

---

### Post by rishabhjain23 on 2009-02-02
Hi ,

I desperately need some help from you guys.
I tried everything mentioned in above posts by Harry excluding this command :

sudo mv image name /opt/dynamips/images

I am newbie to ubuntu and couldn't run this command. gives some error. May be my image getting downloaded elsewhere. However I manually moved the image to speicifed folder. I did all installation from root account. I checked all file permission as well. local host process at 7200 works but when I try to open .net file in dynagen , it gives me error " error opening the file: couldn't open .net file".
i double checked all permissions and path and nothing is wrong according to me. I have no problem running dynamips in xp but on ubuntu it doesnt work.
Pls help as I have booked ccie written for next week.

---

### Post by geezerone on 2009-04-01
Don't have medibuntu repo but found [THIS]("http://www.the-little-things.net/blog/?p=16") site which worked in getting GNS3 to install. He creates folders within /opt/ and then sets these folders within GNS3 preferences once up and running - easy!

Only thing I can see is that trying to console brings a console window -

```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connected to Dynamips VM "R0" (ID 0, type c7200) - Console port
```  but nothing after that even when hitting enter?

Any ideas, as GNS3 looks easy to configure and enable the process of learning to take place much easier - after all, I want to be a Cisco expert (like there is such a thing) not a dynamips expert ;)

---

### Post by FirstByté on 2009-06-15
This is a note on how I solved my "Can't start Dynamips on port XXXX" [on my Ubuntu 9.04]

I installed GNS3 through terminal:
```

sudo apt-get install GNS3

```

then I made a directory for my IOS in the "/opt" folder

```

sudo mkdir /opt/GNS3/IOS/

```

then I copied the IOS .bin files I downloaded **[[here]("http://downloads.sourceforge.net/gns-3/dynamips-0.2.8-RC2-x86.bin?download")]** into the new folder I created.

```

sudo cp ***<wherever it was downloaded>***/dynamips-0.2.8-RC2-x86.bin /opt/GNS3/IOS/

```

Change the mode of the file
```

cd /opt/GNS/IOS/
sudo chmod +x ./dynamips-0.2.8-RC2-x86.bin

```


Then, fire the GNS3.

Go to Edit->Preferences *or **Ctrl+Shift+P***
->Dynamips/Settings
* Under the "Executable Path" 
      redirect it to our "/opt/GNS3/IOS/dynamips-0.2.8-RC2-x86.bin"

* leave "Working directory" as "/tmp"

* Base Port: 7200; Base UDP: 10000; Base console: 2000

->Hypervisor Manager/Settings

* Uncheck "Use Hypervisor Manager when importing"

Run a test :popcorn:

**"Dynamips successfully started"**:)
*listen to some jazz!*

---

### Post by RealG187 on 2010-05-07
I don't have a Cisco login. Is there a way for me to get the images?

Are the images not allowed to be distributed? If they are, are there clone images not copyrighted by Cisco that act the same way (kinda like how Linux was a clone of Unix).

I am taking a networking course and reading about the IOS and need a way to practice.

I have a LabSim disk that emulates the IOS, but it's only for the labs. I need something where I can just try whatever I want until I learn enough to do the labs.

I paid for the book, so I am not stealing from Cisco. Is there a way to extract the images from the LabSim disk?

---

