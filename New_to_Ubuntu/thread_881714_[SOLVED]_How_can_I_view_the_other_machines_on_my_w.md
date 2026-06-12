---
title: "[SOLVED] How can I view the other machines on my wireless network?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Happibun on 2008-08-06
Hi.

I'm using 8.04 on my laptop. I am connected to a wireless network at home using Wicd instead of network manager (long story involving a Broadcom chipset and lots of heartache). My router is a Netgear. 

Every so often I need to look at what devices are on my network (partly because I am hunting down a networked printer which I'm having a devil of a time assigning  a static address to). There must be a simple command out there, or even some GUI way, but I have not figured it out. 

I've spent most of 5 hours on this, and my head hurts. Please rescue me.[-o<

Thanks

---

### Post by iaculallad on 2008-08-06
What about using the nmap utility?

```
sudo apt-get nmap
```

And, after installation - ping scan your network:

```
nmap -sP 192.168.5.0/24
```

Change the value of 192.168.5.2/24 to match your network address.

---

### Post by Happibun on 2008-08-06
Thank you Iaculallad,

I did as you said (although I went throught Synaptic Package Manager to instal nmap because the Terminal still confuses me).

Then I did this:-

> jo@*:~$ nmap -sP 192.168.1.10

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-08-06 17:54 BST
Host 192.168.1.1 appears to be up.
Nmap done: 1 IP address (1 host up) scanned in 0.154 seconds


Which tells me that my router is up and running :), but not what address my printer has been assigned by the router. :(

Have I missed the point or done something wrong?

Awfully sorry, I don't want to sound ungrateful.

---

### Post by cariboo on 2008-08-06
Yes you did try:

```
nmap sP 192.168.1.0/24
```

This will find all the computers/printers, anything with an ip address
on you network.

Jim

---

### Post by halitech on 2008-08-06
I did it just to test and here are my results
```

daryl@ubuntu:~$ nmap -sP 192.168.0.0/24

Starting Nmap 4.53 ( http://insecure.org ) at 2008-08-06 15:17 ADT
Host 192.168.0.1 appears to be up.
Host 192.168.0.100 appears to be up.
Host 192.168.0.101 appears to be up.
Host 192.168.0.103 appears to be up.
Nmap done: 256 IP addresses (4 hosts up) scanned in 9.542 seconds
daryl@ubuntu:~$ 

```

make sure you are using the correct IP address layout or it won't work

---

### Post by cgkades on 2008-08-06
You should be able to statically assing an ip addres using your router. You will need to know the MAC address of the network card in your printer, but you should be able to get that from nmap, wireshark, or from your router.

---

### Post by halitech on 2008-08-06
> 

Every so often I need to look at what devices are on my network (partly because I am hunting down a networked printer which I'm having a devil of a time assigning  a static address to). 
Thanks

what kind of printer is it?

---

### Post by caljohnsmith on 2008-08-06
Happibun, I made a bash script for myself some time ago for doing a simple ARP scan along with DNS name lookup of every host on the LAN. An ARP scan is the most reliable way to discover all hosts on a LAN, because not all computers will respond to ping requests because of their firewall software. And the DNS lookup will tell you the computer/printer/host's name as it is found in your router's DHCP table, which is really useful in identifying which IP goes with which computer/printer/etc.

You might like it because it is GUI, nothing to configure (after you set a few things in the script), just run it and it will scan all addresses on your subnet. You can run it either at the command line (it will pop up a GUI window), or do like I do and set up a menu entry for it. Instead of using nmap (which is a great all-around port-scanning tool and such), the script uses a tiny program "arp-scan" which you can get through the repositories. If you want to give it a whirl, here it is:
```

#!/bin/bash

{
echo "Beginning the ARP scan; this will take approximately 15 seconds..."
echo
arp-scan --retry 10 --interface [COLOR="Blue"]wlan0[/COLOR] --localnet | tee /tmp/arpscan.tmp
echo
echo "ARP scan finished."
echo "================================================="

cat /tmp/arpscan.tmp | grep [COLOR="Blue"]192[/COLOR] | awk '{print $1}' | while IFS=$'\n' read IP_addr; do
	
	if [  ${IP_addr#*.*.*.*} != 1 ]; then
	echo "There are other computers on the LAN." >> /tmp/arpscan.tmp
		if [ "$echo_begin_scan" != "false" ]; then
		echo "DNS query results for each host:"; echo
		fi
	echo_begin_scan="false"
	Gateway_IP=$(route -n | grep UG | awk '{print $2}')
	host_name_with_domain=$(nslookup $IP_addr $Gateway_IP | grep name | awk '{print $4}')
	host_name=${host_name_with_domain%%.*}
	echo "$IP_addr = \"$host_name\""
	fi
done

if [ "$(tail -n 1 /tmp/arpscan.tmp)" != "There are other computers on the LAN." ]; then
	echo "DNS lookup skipped; only the gateway responded to the ARP scan."
fi

} | zenity --text-info --width=600 --height=500 --title="ARP Scan with DNS lookup"
rm -f /tmp/arpscan.tmp


```
My wireless interface is wlan0, if yours is different, you can change it above as highlighted. Also, if you are using a different subnet then 192.x.x.x then you'll have to change the 192 above. Just save it to a file, say "WLAN_scan.sh", and then make it executable:
```
chmod +x WLAN_scan.sh

```
And then run it with:
```
./WLAN_scan.sh
```

---

### Post by Blutack on 2008-08-06
I tend to use nmap with the -O options instead.  That way it tries to work out what the OS of the thing it's pinged is, and you can normally work out what the printer is through elimination.
Just try
sudo nmap -sOP 192.168.0.0/24

---

### Post by Happibun on 2008-08-06
OoooooooooKaaaaaaaaay.

Lots to take on board here. Thank you all for responding, lets chip away at this one bit at a time so you can see how I'm progressing.

**Iaculallad** > Sorry, I misunderstood 
> Change the value of 192.168.5.2/24 to match your network address.
to mean that I just replaced the numbers with my network address, I did not understand what the /24 stood for, and assumed it was something to do with your personal network address :oops: .

What does the /24 mean then? I can see what it does now, but I don't know why 	:-k

Incidentally > :~$ nmap sP 192.168.1.1/24
 got me a nice little list of what 'interesting' ports were doing on individual devices, but not the addresses of the devices.
> :~$ nmap -sP 192.168.1.1/24
 Got me a list of the router, two PCs, and the printer that happen to be on at the moment :) Yay

**cgkades & halitech** > The printer is an old USB Samsung laser printer which runs on the network through an Apple Airport Express. I have the Mac address for the airport, and assigned a fixed network address high up past 192.168.1.200 within the router. I then told the router not to dynamically assign addresses above 192.168.0.200 (because that is what I thought you had to do). The next time I reset the router, it had assigned the printer to something like 192.168.1.13, I don't know why, but it was not what I thought it was supposed to do 	:x

So I reset the DHCP settings to 192.168.1.10 to 192.168.1.254 again. The printer still sits up in the 192.168.1.200s (192.168.1.213 as I have now confirmed) and I know that it is unlikely to have it's address assigned to anything else, so I guess that is good enough, if messy.

The next stage is for me to make sure I have told CUPS everything it needs to know...  :?

But back to the network thing. I decided to have a look at **Blutack's** suggestion and tried 
> sudo nmap -sOP 192.168.1.1/24
Which produced -
> Sorry, the IPProtoscan, Listscan, and Pingscan (-sO, -sL, -sP) must currently be used alone rather than combined with other scan types.

So I tried 
> sudo nmap -sO 192.168.1.1/24
Which, after a considerable pause, gave a me a lovely list including MAC addresses IP addresses, Protocols (another name for ports?), and operating systems.

I like the idea of having a script, and decided to take **caljohnsmith** up on his offer. Here we run in to the next typical problem for the newbie...

I saved the script (interface wlan0 and my network starts with 192, so I am assuming I need make no changes here), but when I tried to compile it, I was informed - chmod: cannot access `WLAN_scan.sh': No such file or directory

I did I save it in the wrong place? Which folder should I save it to? I am confused again :cry:

Sorry.

Jo

---

### Post by iaculallad on 2008-08-06
/24 is a notation. It can be translated to 255.255.255.0, your subnet-mask for your local private IP'd network.

Just be sure that you're inside the same directory as the script before issuing the command below to make give it an executable attribute:

```
chmod +x WLAN_scan.sh
```

EDIT: You can save the script in your /home directory or on your Desktop.

---

### Post by caljohnsmith on 2008-08-06
Happibun, just do like iaculallad said to get my script working. But first install that arp-scan program:
```
sudo apt-get install arp-scan
```
Then if you save that script to your desktop for example, here is exactly what you would do:
```

cd ~/Desktop
chmod +x WLAN_scan.sh
./WLAN_scan.sh

```
In other words, just "cd" into whatever directory you decide to save it in and then run the other two commands.

---

### Post by lswb on 2008-08-06
If the netgear router is doing DHCP for your net, you should be able to find a list of connected clients by accessing the router admin pages.

---

### Post by jimrz on 2008-08-06
Most Netgear routers have a web based setup utility that is easily accessed via your browser.

 Their default ip for the browser is 192.168.0.1 (check your manual to   confirm and also get the user name and password for login). Then in you browser address window enter
 ```
http://192.168.0.1
```
which should bring you to a login screen. Once in, look for "Attached Devices" where you should see a list of every thing on your network showing device name/mac addy/ip addy. 

 Many routers also allow you to "reserve" ip addresses for specific machines by device name/mac addy. Look for "LAN IP setup" (or similar) to see if yours does. If so, you can easily set it to give your printer the same ip each time. This allows you to have "static ip" functionality when desired while still using dhcp. This is also handy for laptops as you can leave set for dhcp and still have a functionally static ip on your home network.

---

### Post by Happibun on 2008-08-07
Good morning gentlemen,

Well, it is morning here (when I started typing this, it is PM now...), and I have got my first cup of coffee, and the lappy booted up all ready for the next day of OS wrangling. Let me try and gather my braincell a bit... 	:p

Last night I located and installed arp-scan using the Synaptic Package manager, then I saved **caljohnsmith's** code to a directory in my home folder. 

This morning, once I'd navigated to it :oops:, I got it compiled absolutely fine \\:D/.

However, perhaps I do need to look at the code again, because once I ran it, it does not seem to be looking at the right thing. This is what I got -
> jo@*:~/Programs$ ./WLAN_scan.sh
You need to be root, or arp-scan must be SUID root, to open a link-layer socket.
link_open: Operation not permitted
jo@*:~/Programs$ sudo ./WLAN_scan.sh
[sudo] password for jo: 
ioctl: No such device


I need to do a quick **iwconfig**: Yup, I told it to look at the wrong thing.
> jo@*:~/Programs$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"*****"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:7D:2A:52   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=63/100  Signal level=-50 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Doh! Back to modify the script, my network is eth1, not wlan0. 

Here's a thought, and I know that it probably rates on the same level as my mum thinking that electricity leaks out of unoccupied sockets if you don't switch them off, but since I compiled an incorrect script, will that remain lurking about in my laptop ready to cause me problems, or will it get overwritten when I recompile? Er, you know, have I broken anything? I'm so used to the loose ends and dirty uninstals you get with Windoze, I can't really believe I have not managed to break or damage my installation yet...

Yeah I know, I'm being very, very, blonde. Which conveniently takes me to the posts by **lswb and jimrz**. You are absolutely right, the easiest and most straight forward way to see a list of all the machines (except the router, because it does not list itself) is by looking at it through the router admin pages with my browser. I could, to save a lot of keyboard wear and tear, say that I had completely forgotten about that route and leave it at that But the truth is that I'm deliberately trying to do things the hard way to see if I can possibly learn something, and boy do I have a lot to learn!

Right, I'll stand back and wait for the first volley of rotten tomatoes, or whatever else it is you throw at dingbats in Ubuntuland. 8-[

I have been using Ubuntu for almost a year, but I still rate myself as an absolute beginner because I don't know anything about what goes on 'underneath', and quite honestly, when something does not do what I expect it to (which is not very often I hasten to add), I don't know why, or how to fix it. Honestly, IMHO it is a good thing that someone can install a new OS and work with it like that. Like the majority of car drivers, most people don't ever want to know what is doing what, they just want it to go and do what they want without hassle. There is a big difference between a driver and a mechanic.

I am, like most people I guess, GUIcentric, because I don't remember what seem to me to be a whole lot of random commands, and I don't understand the Terminal as a consequence of that (I'm also dyslexic - a major downside when trying to remember letter sequences - but thank gawd for spell checkers eh?) :). The best way for me to learn something is for me to take on a project, roll up my sleeves, and jump right in. Getting my printer networked, and reliably interfaced with this laptop is just one of those projects. 

Windows seems to cope fine with dynamic addresses, it also has a network thingie which shows you your network without having to delve in to the router's administration pages. Linux seems to like static IP addresses, and I was wondering if there was a way of looking at the network through the OS rather than the browser. So, given that there are many ways to crack a nut, and that many people feel that this is one of the great strengths of Linux, I wanted to explore them. I know I didn't make that very clear with my original query, but I didn't want to make it sound like I was asking for too much. [Waits for second volley of tomatoes 	:neutral: ]

I am hoping that if I thrash about a bit, I'll learn something that will stick, and perhaps one day I'll be able to help someone else when they are at the stage I am at now.

Attached is a picture of the arp_scan output. 

I'm off to play with CUPS now.

Thank you all very much, I am indeed a Happy Bunny 
:popcorn:

---

### Post by caljohnsmith on 2008-08-07
Happibun, I forgot that I had set the "s" bit on that arp-scan program so I could run it as root without it asking for a password every time I ran my script. Now I'm sure that someone or the moderators will point out that doing that is not generally recommended as it could *possibly* lead to a security risk if somehow that arp-program allows shell escapes or something similar. But if you are the only one who uses your computer (or trust others who use it), it is a perfectly legitimate way to run that program without it always nagging you for a root password. Here is how you would do it:
```
sudo chmod u+s /usr/bin/arp-scan
```
If you would rather enter a password every time you run the program instead, then just do like you originally did:
```
sudo ./ARP_scan.sh
```
That should fix that problem.

And by the way, the "ARP_scan.sh" is what is called a "shell script", meaning it is essentially just a bunch of shell commands that are run as a program. "Shell commands" are any commands you enter into a terminal, like "cd", "ls", etc. And that "chmod" command merely makes the "ARP_scan.sh" executable (runnable), and does not compile the program. Thus when you make changes to that ARP_scan.sh file, there's no need to run the "chmod" command again or "recompile." Just change the file, save, and run the script again. :)

From that screen shot you attached, it looks like the DNS lookup part of that script didn't work with your router. To see if your router supports DNS lookup for hosts on the LAN, please try the following:
```
nslookup 192.168.1.10 192.168.1.1
```
The first address is the computer you want to look up a host name for, and the second address (192.168.1.1) should be the address of your router. Also try 192.168.1.213 instead of 192.168.1.10 in the above example, and copy/paste the results back here.

---

### Post by Happibun on 2008-08-07
Thank you **CalJohnSmith,** you are a star! 	:KS

That is exactly the kind of clarity I need, I was not sure what Shell Script was, or how it related to Terminal or Bash, but now I have a better idea. In the end, I did run the "chmod" command again, because I did not know any better. The lappy still works, so what the hey. :-\"

Anyhow :idea:, does this mean I could make a shell script for the commands I need to run every time Ubuntu gets updated and I have to remove Network Manager, install Ndiswrapper, and Wicd to get myself back on line wirelessly? Because by gum it is a pain having to type them every time given my banana fingers and bad sprelling 	:)

Also: Would that mean there is some way I could automate the log in to the network every time I boot up? I think I might be getting an inkling of the idea, and my jaw is dropping with the awsomeness (Is that a word?) of it all.

Oh wow.... :shock: =D>

OK, better snap out of that and get back on track before my brain melts with joy.

The result for **nslookup 192.168.1.10 192.168.1.1** goes like this:
> jo@*:~$ nslookup 192.168.1.10 192.168.1.1
Server:		192.168.1.1
Address:	192.168.1.1#53

** server can't find 10.1.168.192.in-addr.arpa.: NXDOMAIN

I was expecting it to bomb on 192.168.1.10, because the router is set not to assign anything from 192.168.1.1 to 192.168.1.10, so the first machine (which happens to be my lappy today) will be assigned 192.168.1.11, and so on.

Given that, I am a bit surprised to find that the command** nslookup 192.168.1.213 192.168.1.1** gives me :-
> jo@*:~$ nslookup 192.168.1.213 192.168.1.1
Server:		192.168.1.1
Address:	192.168.1.1#53

** server can't find 213.1.168.192.in-addr.arpa.: NXDOMAIN


So it looks like you are right, something is broke? What now? 	:-k

~ Jo :smile:

---

### Post by caljohnsmith on 2008-08-07
> **Happibun said:**
> Anyhow :idea:, does this mean I could make a shell script for the commands I need to run every time Ubuntu gets updated and I have to remove Network Manager, install Ndiswrapper, and Wicd to get myself back on line wirelessly? Because by gum it is a pain having to type them every time given my banana fingers and bad sprelling 

Also: Would that mean there is some way I could automate the log in to the network every time I boot up? I think I might be getting an inkling of the idea, and my jaw is dropping with the awsomeness (Is that a word?) of it all.

Oh wow.... :shock: =D>
Yes, Jo, you hit the nail on the head--that's exactly what is so useful and "awesome" about shell scripts--everyday users like you and me can automate a whole bunch of commands, or even make them into useful programs. :) Most likely you can automate all those commands you alluded to by putting them in a shell script.

Also, if you decide you like the results that nmap gives you more then the ARP scan results that my script gives, you can always put nmap into a shell script and even popup a window with its results similar to my script. As you can see, there are lots of possibilities with the power of shell scripts.
> **Happibun said:**
> The result for **nslookup 192.168.1.10 192.168.1.1** goes like this:

I was expecting it to bomb on 192.168.1.10, because the router is set not to assign anything from 192.168.1.1 to 192.168.1.10, so the first machine (which happens to be my lappy today) will be assigned 192.168.1.11, and so on.

Given that, I am a bit surprised to find that the command** nslookup 192.168.1.213 192.168.1.1** gives me :-


So it looks like you are right, something is broke? What now? 	:-k

~ Jo :smile:
Just to clarify, I asked you to use 192.168.1.10 and 192.168.1.213 because those are the hosts that responded to your ARP scan, according to that screen shot you posted previously. The only point was to pick a LAN address of a known host (192.168.1.X) and try to do a DNS name lookup with your router. But, it doesn't look like your router supports that feature. 

Now that you're not afraid of shell scripts and can see their usefulness :), you might want to try this variation of the ARP_scan.sh that I also wrote a few months back:
```
#!/bin/bash

{
echo "Beginning the ARP scan; this will take approximately 15 seconds..."
echo
arp-scan --retry 10 --interface [COLOR="Blue"]wlan0[/COLOR] --localnet | tee /tmp/arpscan.tmp
echo
echo "ARP scan finished."
echo "============================="

cat /tmp/arpscan.tmp | grep 192 | awk '{print $1}' | while IFS=$'\n' read IP_addr; do
	
	if [  ${IP_addr#*.*.*.*} != 1 ]; then
	echo "There are hosts to scan for NetBIOS names." >> /tmp/arpscan.tmp
		if [ "$echo_begin_scan" != "false" ]; then
		echo "Beginning NetBIOS name lookup for each host..."; echo
		fi
	echo_begin_scan="false"
	nmblookup -A $IP_addr &
	fi
done

if [ "$(tail -n 1 /tmp/arpscan.tmp)" != "There are hosts to scan for NetBIOS names." ]; then
	echo "There are no hosts to query for NetBIOS name lookup."
fi

} | zenity --text-info --width=600 --height=500 --title="ARP & NetBIOS Scan"
rm -f /tmp/arpscan.tmp
```
The only thing you will need to change is the wlan0 I think. Instead of using DNS to lookup names of hosts, it uses the Windows NetBIOS protocol to get host names; therefore it will only return names of Windows computers, or other computers that have NetBIOS name lookup capability (Ubuntu can do this with the right packages installed). If you want to give it a try, first install:
```
sudo apt-get install samba-common
```
Let me know how it goes if you have any problems.

---

### Post by Happibun on 2008-08-07
Ooooooooooo, epiphany.  :guitar:

I must learn what all these gobldy gooky things mean, so I can drive this OS properly. Actually that is one of the reasons I am afraid of it - with good reason, I know it is really powerful, and the wrong combination of letters could kill my set up completely and wipe my data. I don't know enough, and blundering about is a pretty dangerous way of going about things. [Click here to see the dangerous code post.]("http://ubuntuforums.org/announcement.php?f=326")

I see that I am going to need a really good guide to the terminal, some idea of the structure of Linux hierarchy, and a script manual. I will have a good footle in the forums, and see what I can find on Google later on, there's bound to be something that's really step by step out there, but if anyone has a good recommendation, I'll be happy to hear it. :)

Anyhow, sorry that's a bit off topic, back to the network.

My router is an old Netgear DG834GT running firmware V1.02.13, which it informs me is the latest version. I inherited it from my previous workplace, in the days before I knew anything at all about networking. My boss installed it so that my home network was the same as the work one and the windows machines didn't need any tweaking between the two environments. I've changed most of the settings since then, but keeping the first 9 addresses free is a left over from that company. I've operated on the 'If it ain't broke, don't fiddle with it' principle. Well actually I lie, I've fiddled and broken it (and sort of mended it again) lots in other areas, but that original bit remains because it has not bugged me enough yet... And I have a *little* bit of understanding about my network now. 8-[

I already have samba-common installed and running on the lappy, so I didn't need to go get it. I modified the script, and ran it, and got the output shown in the picture attached.

The printer (via the Apple Airport) did not respond, but then I don't know if it is supposed to? 

What are your thoughts on this output?

Thanks, Jo

---

### Post by Happibun on 2008-08-07
FYI, relevant shots of the router settings. Give me a shout if you want more.

Interesting how the Windoze machine hops in at 10 whilst mine comes in at 11. Mine was on the network first this morning, but 10 is not an assigned address.

Hmm :-k

Jo ~

---

### Post by caljohnsmith on 2008-08-07
Looks like you got the script running perfectly, Jo. :) From that screen shot you posted, we can see three other hosts on the LAN besides the computer you ran it from: 
[LIST]
[*]192.168.1.1 is simply your router of course, easily verified because the ARP scan says its manufacturer is "Netgear". 
[*]192.168.1.10 is called "AS-IT-PC0004" according to NetBIOS. If you go into your Windows settings on that 192.168.1.10 machine, I think Start > Control Panel > System, you will see that's the name of that computer.
[*]192.168.1.213 is your Apple printer, which we can surmise from the ARP scan which says the manufacturer is "Apple Computer". And of course it won't respond to a Windows protocol like NetBIOS--heaven forbid there be any compatibility between Apple and Microsoft. :roll:
[/LIST]
Now if you right-click on the Applications menu on your desktop, choose menu editor, you can add a menu item for that ARP/NetBIOS scanner script if you like; where it asks for the command to run, simply use:
```
gksudo /path_to_script/ARP_Netbios_script.sh
```
That way you don't even have to touch the command line--simply run the script from the menu.

Anyway, let me know if you have more questions, but does that script solve your original question? If so it would be a good idea to mark the thread as "solved."

---

### Post by caljohnsmith on 2008-08-07
> **Happibun said:**
> FYI, relevant shots of the router settings. Give me a shout if you want more.

Interesting how the Windoze machine hops in at 10 whilst mine comes in at 11. Mine was on the network first this morning, but 10 is not an assigned address.

Hmm :-k

Jo ~
Actually from those screen shots, the DHCP start address is 192.168.1.10, so yes, 192.168.1.10 can be assigned to a host. Also, once a host gets an IP address via DHCP (Dynamic Host Configuration Protocol), it keeps that address for whatever the "lease period" is set in the router settings. That's why that Windows machine got the 192.168.1.10 address again even though you connected first.

---

### Post by Happibun on 2008-08-07
> **caljohnsmith said:**
> Actually from those screen shots, the DHCP start address is 192.168.1.10, so yes, 192.168.1.10 can be assigned to a host. Also, once a host gets an IP address via DHCP (Dynamic Host Configuration Protocol), it keeps that address for whatever the "lease period" is set in the router settings. That's why that Windows machine got the 192.168.1.10 address again even though you connected first.

Ah, that's partly my fault for not knowing the right terminology. What I meant was that 192.168.1.10 was not a permanently assigned address, but you've solved another mystery for me. I'd forgotten about the 'lease period', which explains why it is behaving like a static allocation for the time being.

> 192.168.1.10 is called "AS-IT-PC0004" according to NetBIOSYup, like the router it was also inherited from the ex company, I never bothered to change it's name.

> 192.168.1.213 is your Apple printer, which we can surmise from the ARP scan which says the manufacturer is "Apple Computer". And of course it won't respond to a Windows protocol like NetBIOS--heaven forbid there be any compatibility between Apple and Microsoft. :roll:Indeed. Sigh.  ](*,)

> Anyway, let me know if you have more questions, but does that script solve your original question? If so it would be a good idea to mark the thread as "solved."It does indeed, and I have done so. Thank you so much for your help, and again to the others who contributed too. It has been a great journey, and a very useful introduction to what this amazing OS can do.

Respect, and best wishes, Jo

---

