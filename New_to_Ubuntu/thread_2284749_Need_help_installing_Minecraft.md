---
title: "Need help installing Minecraft"
date: 2015-07-01
forum: New to Ubuntu
---

### Post by jeff131 on 2015-07-01
Hello All,

I have had some trouble installing Minecraft. I searched up how to do it on [this]("http://www.everydaylinuxuser.com/2013/12/how-to-install-minecraft-for-ubuntu.html") page, but the commands, and double clicking did not work. Am I doing it wrong? Is there another way? By the way, I have Ubuntu 14.04 installed from a USB.

Thank you,

-Jeff

EDIT- I found out on the Minecraft webpage that you need Oracle JVM. What is that? Where can you download it?

Thank you

EDIT 2- Solved, I found out I had to use OpenJDK 6 for it to work by double clicking.

---

### Post by sandyd on 2015-07-01
Hi, we will need some more information. When you run the commands```

java -jar Minecraft.jar
```

What shows up in the terminal?

---

### Post by jeff131 on 2015-07-01
> **sandyd said:**
> Hi, we will need some more information. When you run the commands```

java -jar Minecraft.jar
```

What shows up in the terminal?

Oh, my apologies. When I run```
java -jar Minecraft.jar
```, it says "Error: Unable to access jarfile Minecraft.jar in the terminal. For my Java on Ubuntu, I have OpenJDK Java Runtime. Just so I am not being dumb, would this work for running Java, for a game like Minecraft? I followed the instructions for OpenJDK on the link on the original post. For the line of code, ```
[COLOR=#333333][FONT=Courier New]chmod +x Minecraft.jar[/FONT][/COLOR]
```, it said "chmod: cannot access ‘Minecraft.jar’: No such file or directory"

Thank you,

Jeff

---

### Post by cariboo on 2015-07-01
What if you use the full path to where Minecraft.jar is located? eg:

```
java -jar /usr/games/Minecraft/Minecraft.jar
```

Don't use my example, as I don't have Minecraft installed, and I have no idea what directory it is installed to.

---

### Post by GrouchyGaijin on 2015-07-02
It does sound like your jar file is not set to execute
You need to include the full path to the file you want to make executable.
In my case Minecraft is located at:
```
/home/john/Downloads/MC/Minecraft.jar
```

Just to make this easier I created a link to the jar file and placed it on my desktop.

---

### Post by mastablasta on 2015-07-02
right click .jar, properties and set it as executable. problem solved.

---

### Post by Kale_Freemon on 2015-07-02
I found a much simpler way that worked great on 14.04 and 15.10. I had a lot of problem getting Minecraft to run on Ubuntu the official way.

What I did was install Minecraft Installer, which worked great and I've been playing Minecraft with zero problems on my 15.10 install.

[http://www.omgubuntu.co.uk/2013/04/minecraft-installer-for-ubuntu](http://www.omgubuntu.co.uk/2013/04/minecraft-installer-for-ubuntu)

---

### Post by jeff131 on 2015-07-02
> **Kale_Freemon said:**
> I found a much simpler way that worked great on 14.04 and 15.10. I had a lot of problem getting Minecraft to run on Ubuntu the official way.

What I did was install Minecraft Installer, which worked great and I've been playing Minecraft with zero problems on my 15.10 install.

[http://www.omgubuntu.co.uk/2013/04/minecraft-installer-for-ubuntu](http://www.omgubuntu.co.uk/2013/04/minecraft-installer-for-ubuntu)

Hi, I tried your method, but there were some errors. Here are all the lines of code that have errors (I believe) ```
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US         
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US     
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US 
Ign http://ppa.launchpad.net trusty/main Translation-en            
Fetched 3,175 kB in 9s (350 kB/s)                                              
W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Thank you,

Jeff

---

### Post by GrouchyGaijin on 2015-07-02
Wow I did not realize that installing Minecraft was an issue for so many people.
Did I just get lucky?

I installed the JDK Java 6 runtime and then downloaded the Minecraft demo: [https://minecraft.net/demo](https://minecraft.net/demo)
I had to create a Mojang account first, but then I downloaded the demo.
I then made the Minecraft.jar file executable after that I right clicked the jar file and chose open with JDK Java 6 runtime.

The most difficult part was creating the Mojang account.
Well, that and playing the 19.95 EUR for the full version after the demo expired.
I should say 19.95 EUR x 2 because after successfully installing and playing Minecraft on one computer my kids really wanted Minecraft on their Xbuntu machine so that they could play together on our wifi network.  (The thing I don't understand is that Mojang is a Swedish company, but I had to pay in Euros - using Crowns would have been cheaper as there is no conversion fee from the bank.)

---

### Post by jeff131 on 2015-07-02
You said your kids wanted Minecraft as well? You only need to pay for Minecraft once, and you can have it on all machines! When you are on the page, look at text that says, "Already bought the game?" And you will see a link below it that leads to a download page to download the launcher, no need to buy it again for another machine. I have Minecraft on three computers, with no extra cost!

---

### Post by GrouchyGaijin on 2015-07-02
No kidding?  And you can use all three at the same time?  Glad I didn't set it up on a third machine then.

---

### Post by Kale_Freemon on 2015-07-03
The PPA that seems to be having a problem does not appear to be for the Minecraft Installer. It looks like it's for Gwibber-Daily.

Sure you entered in the PPA correctly? Check your software sources.

---

