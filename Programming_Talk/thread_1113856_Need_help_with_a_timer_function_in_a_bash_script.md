---
title: "Need help with a timer function in a bash script"
date: 2009-04-02
forum: Programming Talk
---

### Post by UtopiaTheory on 2009-04-02
Hey everyone...I have been working on this bash script that is a hacking/cracking simulation.  It simulates cracking your way into an NSA server.  Lots of fun if you have prying eyes over your shoulder.  Anyways, I'm trying to add a function that starts a silent timer after the user ssh's into the remote server.  After 3 minutes, I want it to kill the fake connection and say that the authorities have been notified and such.  Here's the script as it is now.  Feel free to try it.  When you run the script you will get what looks to be a regular terminal prompt (except that the hostname is slax).  Type help to see the commands available.  They have to be typed exactly to work:

```

#!/bin/bash
#lethal-0.02
#a script by DeX to make anyone look like a real haxor! OMG!!1
############

#set starting variable for hostname
hozt='slax:~$'

#emulate the prompt
clear;

read -p "root@"$hozt" "  command
while [[ $choice != 0 ]]
do
   
case $command in

#nslookup
    'nslookup nsa.gov') sleep 1;
    echo "Server:      204.14.141.218";
    echo "Address      204.14.141.218#53"
    echo
    echo "Non-authoritative answer:"
    echo "Name:      nsa.gov"
    echo "Address:   67.15.6.98"
    ;;

#ping
    'ping 67.15.6.98') sleep 1;
    echo "PING 67.15.6.98 (67.15.6.98) 56(84) bytes of data."
sleep 1;
    echo "64 bytes from 67.15.6.98: icmp_seq=1 ttl=52 time=68 ms"
sleep 1;
    echo "64 bytes from 67.15.6.98: icmp_seq=2 ttl=52 time=87 ms"
sleep 1;
    echo "64 bytes from 67.15.6.98: icmp_seq=3 ttl=52 time=87 ms"
sleep 1;
    echo "64 bytes from 67.15.6.98: icmp_seq=4 ttl=52 time=92 ms"
sleep 1;
    echo "--- 67.15.6.98 ping statistics ---"
    echo "4 packets transmitted, 4 received, 0% packet loss, time 334ms"
    ;;

#nmap
    'nmap -sS 67.15.6.98') echo
    echo "Starting Nmap 4.53 ( http://insecure.org ) at" $(date)
sleep 4;
    echo "Interesting ports on 67.15.6.98:"
    echo "Not shown: 1712 closed ports"
    echo "PORT   STATE   SERVICE"
    echo "80/tcp   open   http"
    echo "443/tcp   open   https"
    echo "MAC Address: 00:11:25:99:17:22 (Fortress Networks)"
    echo
    echo "Nmap done: 1 IP address (1 host up) scanned in 4.399 seconds"
    ;;

#dscan
    'dscan -fS 67.15.6.98:443') echo
    echo "dScan probing 1 host"
    sleep 4
    echo "https on port 443 is vulnerable!"
    echo "please run updates to correct this security problem!"
    ;;

#metasploit
    'metasploit -script https443.sh -i 67.15.6.98') echo
sleep 1
echo "        -module -export-dynamic   -o rlm_perl.la  "
echo "        -rpath /usr/local/lib rlm_perl.lo rlm_perl.c bradius.la"
echo "        `perl -MExtUtils::Embed -e ldopts` -lnsl -lresolv  -lpthread"
echo "metasploit framework searching for vulnerable port"
sleep 3
echo "metasploit script successfull!"
echo "run dump to view results"
    ;;

#dump
    'dump -script https443.sh -c pw -U root') echo
sleep 1
echo "root - 0xC23413A8A1E7665fAAD3B435B51404EE"
    ;;

#hydra
    'hydra -b 0xC23413A8A1E7665fAAD3B435B51404EE') echo
sleep 5

#spinner
function spin {
    echo -n '-'
    echo -ne '\b|'
    sleep .1
    echo -ne '\bx'
    sleep .1
    echo -ne '\b+'
}
for i in `seq 1 20` ; do spin; done
echo ""


echo "password match found!"
echo "aRrf349J$"
    ;;

#ssh to nsa
    'ssh -l root 67.15.6.98')  
sleep 5

	read -s -p "Password for root: " pwf

sleep 4
clear
echo "         WARNING!"
echo "This is a Government computer system.  Any"
echo "attempts to access this system by unauthorized"
echo "persons is against the law and will be prosecuted."
echo
sleep 1;

#change the hostname
hozt='nsa.gov:~#'
    ;;

#ls -l
    'ls -l') 
sleep 1
echo "total 12"
echo "drwxr-xr-x 2 root root 4096 $(date) bin"
echo "drwxr-xr-x 2 root root 4096 $(date) docs"
echo "drwxr-xr-x 2 root root 4096 $(date) logs"
    ;;

#cd bin
    'cd bin')
hozt='nsa.gov:~/bin#'
    ;;

#ls
    'ls')
echo "defcon_launch.sh"
    ;;

#defcon_launch.sh
    './defcon_launch.sh') echo
sleep 1

read -p "Username: " uzer
sleep 1
read -s -p "Password: " pwz
sleep 2
echo ""
echo "#################################"
echo "#                               #"
echo "#    DEFCON LAUNCHER STARTED    #"
echo "#                               #"
echo "#################################"
echo ""
echo "Hello Mr. President..."
read -p "How many ICBMs? " missles
read -p "Please Enter GPS Coords: " coords
echo "Defcon Launch Sequence Started"
read -p "Please Enter Verification Code 4: " verificationz
read -p $missles" ICBMs to strike $coords; Are you sure?(Y)or(n)" confirmationz

function spin {
    echo -n '-'
    echo -ne '\b|'
    sleep .1
    echo -ne '\bx'
    sleep .1
    echo -ne '\b+'
}
for i in `seq 1 20` ; do spin; done
echo ""

echo "ICBMs Launched"

function spin {
    echo -n '-'
    echo -ne '\b|'
    sleep .1
    echo -ne '\bx'
    sleep .1
    echo -ne '\b+'
}
for i in `seq 1 20` ; do spin; done
echo ""


sleep 4
echo ""
echo "Target Destroyed, Mr. President."
echo "Exiting program"
;;

#help
    'help')
echo "Commands"
echo "nslookup nsa.gov"
echo "ping 67.15.6.98"
echo "nmap -sS 67.15.6.98"
echo "dscan -fS 67.15.6.98:443"
echo "metasploit -script https443.sh -i 67.15.6.98"
echo "dump -script https443.sh -c pw -U root"
echo "hydra -b 0xC23413A8A1E7665fAAD3B435B51404EE"
echo "ssh -l root 67.15.6.98"
echo "clear"
echo "exit"
echo "**FROM NSA.GOV SHELL FOR REALISM**"
echo "ls -l"
echo "cd bin"
echo "ls"
echo "./defcon_launch.sh"
;;
    'clear')
clear;
;;
    'exit')
exit;
;;
    *)
echo "attack failed; not enough data"
;;
esac

#term again

read -p "root@"$hozt" " command

done

```

Any ideas on the timer?  Do I wrap everything after the ssh in an until loop?  How do I do that without breaking my case loop?  Everything I try breaks it!

---

### Post by SubNetMask on 2009-04-02
> **UtopiaTheory said:**
> 
Any ideas on the timer?  Do I wrap everything after the ssh in an until loop?  How do I do that without breaking my case loop?  Everything I try breaks it!

I don't know shell, but I guess the theory is the same as in C.

Just put in a condition that when the users SSH's, into the server, it logs the current time into a variable, then just make it so that 3 minutes after it calls a statement, like goto:, and displays the message, and keep it into a stand by loop.

Or you can make the condition a case itself

#Time == 3 minutes
display msg
(works in C :P)

I don't know if that makes sense, I program in C and assembly so yeah lol.

---

### Post by UtopiaTheory on 2009-04-03
Thanks man...I'm giving that a shot.  Any Bashers in here have any suggestions?

---

### Post by AnarchyMaster on 2009-04-03
Could always try the sleep command


sleep 180 should do it for 3 minutes

---

### Post by AnarchyMaster on 2009-04-03
*edit*

I miss read, the code would be something like

```
Times = date;
date --date "$Times 3 mins"
until [Times == date]; do
<code here>
done
```
i think should work

---

