---
title: "Ubuntu 9.04 and Mac OS X 10.3.9 Internet Connection Sharing"
date: 2009-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Nyken on 2009-08-12
Ubuntu 9.04 and Mac OS X 10.3.9 Internet Connection Sharing

Writing this how-to for the reason that the other tutorials that I've read about this were for MAC OS X 10.4 
and above. Some of the steps for 10.4 are a bit different than those on 10.3, so I wrote this for those of us
who are fine with 10.3. 

*Soapbox moment* :(

I do wish Apple would stop milking the OS X name to a faretheewell, instead of just making
OS XI and XII - At least Linux and Windows OSes have a name/numerical sucession. It's kinda like Microsoft 
keeping the name Windows 95 for every version made up to now. When looking for an alternative to Windows, 
this reason was one of the main ones I decided to stop at 10.3.9, primarily keep using PCs and just go Linux.

*End moment* 

With this, I'm using a set up that includes a G4 Power PC with a Airport card and a IBM NetVista PC with a 
D-Link DWL G-510 wireless card. My ISP is AT&T and I'm using their cheaper Westell DSL modem connected to the 
Mac.

One - turn on your Mac's AirPort. Make sure it doesn't connect to anything; that it's only on and waiting.

Next: Click the Apple symbol and chose System Preferences > Sharing > Internet

     a) On the line that says "Share your connection from," click on the menu bar and chose Built-in Ethernet
       (or whatever ethernet card you are currently using.)

    b) Then, on the menu that reads "To computers using," place in check next to "AirPort."



Three: Click the button labelled "Airport Options." 

        a) Set up your share by choosing a name, plus a channel on which to broadcast.

    b) Enable WEP (10.3.9 doesn't have WPA natively, as far as I've been able to find) 

    c) Chose a hexadecimal password. It needs to begin with a "$" and have 10 numbers following it. 
       The "$" tells OSX that the number is hexadecimal. This will give you 40-bit encryption.

               Example password: $1234567890
 

Fourth: Click on "Services" on that Sharing Window.

    a) Make sure that Personal Web Sharing is enabled. This service is supposed to be able to give others access 
       to web pages stored on an OSX machine, which I don't pretend to completely understand why this needs to be
       enabled. None of the tutorials I found even mentioned it. It's something I discovered solely going with a
       gut instinct when nothing else was working. This step is critical for your web browser to work - you'll
       be able to ping, traceroute and all that, but not surf, unless you do this.

Fifth:     Now you can go back to Internet and click the "Start" button to start sharing it's connection.


Now, on your Ubuntu machine, do this:

    1) Go to System > Administration > Network and enter your sudo password if asked.

    2) On the window that comes up, chose "Unlock" and enter your sudo password if asked.

    3) Disable roaming, if enabled.

    4) Type in the network name you chose earlier into the ESSID space provided.

    5) Password type is "WEP key (hexadecimal)" Enter the 10-digit password you created on the Mac, just omit the "$"
        
        Example: 1234567890

    6) Connection Settings should be set to "Automatic configuration (DHCP)"

    7) Click "OK."


Your PC should now connect to your Mac and share it's internet connection. :)


Additionally, some Ubuntu set-ups like mine need to have the wireless connection up before the login screen comes up or their
desktop never finishes loading and they get none of those really awesome bongo drums playing. Or maybe you'd like your wireless
up and roaring when you decide to boot into the command line. Well, next is an option that I detailed in another post of mine, 
but this one's modified since for various reasons decided to actually use some kind of encryption this time around.

If you'd like to or need to do this, open your favorite text editor as Root. All of these next steps will need to be done as 
Root, by the way.

1) In the text editor of your choice, we're going to make a small startup script named "won," which is short of "Wireless On."

        This is the script that I use:

        ifconfig wlan0 up
        iwconfig wlan0 essid <name of network>
        iwconfig wlan0 mode managed
        iwconfig wlan0 key <the hexadecimal password you chose without the "$">
        dhclient wlan0

2) Save this script as /etc/init.d/won and make it executable by typing sudo chmod +x /etc/init.d/won


Reboot your computer and all should be well in the world. :cool:

---

