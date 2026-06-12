---
title: "Howto: Kppp on Kubuntu problems."
date: 2006-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2006-11-26
Hi,
     After finding it just about impossible to get Kppp to work properly. I have found that Gnome-ppp is very stable in Kubuntu. The suggestion is to set up wvdial properly and then install Gnome-ppp from the repositories, which is actually a front end for wvdial. It lacks all the bells and whistles that kppp has, but it works. Only use kppp to query the modem as this will always work.
Here are the details for those new to this:
  	 	 	 	 	 	 	 	 	  [COLOR=#000000][SIZE=3]_**Tried and tested good old wvdial:**_[/SIZE][/COLOR]
 [SIZE=3][COLOR=#000000]The most reliable way to get dialed up is via **wvdial** from the konsole, but this means you need to keep the konsole open while you are connected to make sure that you are able to disconnect the modem by typing CTRL+C to disconnect from the telecom line and get back to your normal prompt. If you happen to close the konsole before disconnecting, you may have to reboot your PC to get the modem to disconnect or you may not be aware that you are still connected and run up an account! This can be solved by installing a dial up dialer gui. Some problems may also be picked up when initially configuring wvdial, such as detection of modem.[/COLOR][/SIZE]
  

  [COLOR=#000000][SIZE=3]_In the konsole type:_[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]sudo wvdialconf   /etc/wvdial.conf[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]If this fails due to not finding a modem, it means the modem drivers are not properly installed, but if you can query the modem successfully in Kppp, then it may mean that wvdial cannot see  /dev/modem to set itself up properly. In all cases you may have to open up the file:[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]In Konqueror navigate to  /etc/wvdial.conf, Right click, Actions, Edit as root and change or add the following lines so that the file looks like this below and save:[/SIZE][/COLOR]
  

  [COLOR=#000000][SIZE=3][Dialer Defaults][/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Init1 = ATZ[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Modem Type = Analog Modem[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ISDN = 0[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Phone = xxxxxxxxxxx [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]New PPPD = yes[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Modem = /dev/modem[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Username = yyyyyyyyyyyyy[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Password = zzzzzzzzz[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Baud = 115200[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Stupid mode = on[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]# Carrier Check = no[/SIZE][/COLOR]
  

  [COLOR=#000000][SIZE=3]xxxxxxxxx =  the number to dial up your ISP[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]yyyyyyyyy =  your username supplied by your ISP[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]zzzzzzzzz = your ISP access password[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]In the last line remove the comment # to enable Carrier Check = no if you are using a Smartlink internal modem.[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]You can also add W2 to the Init2 line to show the connection speed if required[/SIZE][/COLOR]
  

  [COLOR=#000000][SIZE=3]_Now go to the console and type:_[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]sudo wvdial[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Once connected see if you can open your browser[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Remember to keep the konsole open while you are connected, you can minimise it if it is in your way.[/SIZE][/COLOR]
  

  [COLOR=#000000][SIZE=3]_To disconnect line while in konsole type:_[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]CTRL+C to end the connection[/SIZE][/COLOR]
  

  [COLOR=#000000][SIZE=3]_Some hints:_[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]If you find that you lose the connection after 30 sec to 3 minutes, then edit pppd.[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Right click on /etc/ppp/options, actions, Edit as root[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Find lcp-echo-interval 30 and lcp-echo-failure 4 and comment both out by adding a # at the beginning of the lines.[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]If you find that you connect successfully, but cannot open any webpages in Firefox then add line default route to /etc/ppp/peers/wvdial[/SIZE][/COLOR]
  

  [COLOR=#000000][SIZE=3]_Adding a gui to wvdial:_[/SIZE][/COLOR]
  

  [COLOR=#000000][SIZE=3]The good news is that there is a nice simple gui for wvdial called Gnome-ppp. This is normally only used in Ubuntu and the name Gnome tends to keep KDE die-hards from installing it on Kubuntu, but it installs straight from the repositories. So once you have wvdial working and you can connect to the internet, enable and update your repositories, use your package manager to download and install Gnome-ppp, right click on the menu icon and create an icon on your desktop. Now rename it so as not to embarrass you as Kubuntu user! to e.g. “Dial up ISP” and it should work very nicely and is definitely more bullet proof than Kppp, even on KDE.[/SIZE][/COLOR]
  

 [COLOR=#000000][SIZE=3]_**Configuring Gnome-ppp:**_[/SIZE][/COLOR]
  

  [COLOR=#000000][SIZE=3]Open Gnome-ppp and click on Setup[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Under Modem tab, Device, you can click detect to have Gnome-ppp detect your modem, but as under the wvdial setup this would maybe not work and you will have to type in your modem device. This could be /dev/modem or /dev/ttyS0 if you have and external modem connected to Com1 or /dev/ttyS1 if on Com2. Here I would suggest using Kppp (the only reliable function that will always work) to Query the modem if you are having problems.[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Under Type select Analogue modem[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Under Speed 115200[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Phone line Tone[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Volume Hi  (speaker volume)[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Dial attempts 1[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Wait for Dial tone checked[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Initstrings and phone number to dial should be picked up from your wvdial configuration, but if not enter them. (see wvdial)[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Under Networking tab[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Leave Dynamic IP Address and Automatic DNS enabled[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Under Options tab[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Check the following items as on, Abort connecting if no dial tone, Check carrier line, Check default route, Ignore terminal strings(Stupid mode). Leave the rest disabled or change any of the settings as your preferences once all is working.[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Close and reopen Gnome-ppp[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Type in your ISP username[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Type in your ISP password[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Check remember password[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Select the number to dial up or type in.[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Now click connect and you should be on.[/SIZE][/COLOR]
 
Hope this makes life more bearable if you are a dialup user.

---

### Post by RabbitWho on 2009-08-22
Does 8.10 already have wvdial? If not could we have some newbie information on how to get it? I think I have it but I'm not sure I have everything I need as on another thread they said to download several things along with it but those things aren't available any more. 

When I type in any command using wvdial what I get is

dev/moden - directory not found 

I'm using a huawei E106G dongel

And to get gnome ppp you said "go to your package manager", I don't know how do do that. 

I know that if I can get gnome ppp working I should be able to connect to the internet using this dongel because I can with Ubuntu but not Kubuntu.

---

### Post by levge on 2009-10-12
sudo apt-get install wvdial
sudo apt-get gnome-ppp
sudo gnome-ppp
in configure it detect automaticly your modem-
but you have to change to usb modem ,
I used stupid mode
it worked for me.

---

