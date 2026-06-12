---
title: "Get your IP from anywhere if you have a cell phone!"
date: 2006-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by SqRt7744 on 2006-03-27
Hi everyone,

I often find myself needing to log into my computer from remote locations.  It would be an easy task if the dynamic IP assigned to me by my internet provider didn't change at the most inopportune moments!  To remedy the situation I wrote a little script to send my IP to my cell phone when it changes.  

Rather than hoarding I'm sharing the wealth.  Hopefully this comes in handy to somebody!

First of all you need smssend!:

```
sudo apt-get install smssend
```

Since my computer is behind a router, I need to find my "world" IP address.  I personally do this with a customized wget/sed/cut script on my router, but to make this non-router specific, I get it here from [www.whatismyip.com](www.whatismyip.com).  Create the file:

```

mkdir ~/bin
cd bin
sudo gedit get_wanip.sh

```

and paste the following into it:

```

#!/bin/bash
wget -O - www.whatismyip.com 2>/dev/null|sed '1,4d;6,177d'|cut -c27-48|cut -d'<' -f1
```

save it, close the text-editor, and make it executable by typing into a terminal:
```

chmod 744 ~/bin/get_wanip.sh
~/bin/get_wanip.sh

```
The last line should have output your IP to the terminal if all went well.
Voila!  If you are displeased with my hack, please make it nicer.  I just whipped it off and am open to criticism.

Now onto the interesting bit: sending the IP to your cell phone.  First of all, you only want the IP sent if it has changed, so the script relies on a subdir from home called .wanip containing a file 'prev_ip'.  To create it:

```

mkdir ~/.wanip
touch ~/.wanip/prev_ip

```

And now the script.  To create it, type
```

gedit ~/bin/send_wanip.sh

```

and paste the following text into the file:

```

#!/bin/bash
previous_ip=`cat /home/YOUR_USERNAME/.wanip/prev_ip`
echo "Previous WAN: $previous_ip"
current_ip=`/home/YOUR_USERNAME/bin/get_wanip.sh`
echo "Current WAN:  $current_ip"
if [ "$previous_ip" = "$current_ip" ]; then
	echo "Nothing to do, IP hasn't changed"
else
	echo "sending sexy new IP to phone(s)..."
	smssend YOUR_PROVIDER.sms 1XXXYYYZZZZ \""$current_ip"\"
	#smssend YOUR_PROVIDER.sms 1XXXYYYZZZZ \""YOUR_USERNAME's IP: $current_ip"\"  
	if [ "$?" = 0 ]; then
		 /home/YOUR_USERNAME/bin/get_wanip.sh > /home/YOUR_USERNAME/.wanip/prev_ip
		 echo "Complete! You should have your new IP shortly."
	else
		 echo "Some random error has occured, WAN IP not sent to cell(s)!"
	fi
fi

```

After you have saved it, be sure to make it executable! To do this, in a terminal type:
```

chmod 744 ~/bin/send_wanip.sh

```

A couple of things to note:  first of all, change YOUR_USERNAME to your own user name and enter your phone number, not the X's, Y's, and Z's I have written!  Second, you can add your friends cell phones as well if you want.  i personally send a copy to myself and my brother, because he stores things on my computer.  Third, you will have to find out the syntax of smssend for your carrier, it varies.  For further info try:
```

man smssend

```

Now setup cron to send you your new IP when it changes! I like the graphical utility called Kcron
```

sudo apt-get install kcron

```
it should now be installed under Applications->System Tools->Kcron.  Add the script as a new task /home/YOUR_USERNAME/bin/send_wanip.sh, select when/how often you want it to run.

Now that you have gone to all the effort of having your IP sent to your cell phone, it's easy to have it emailed to your address of choice (credit goes to magictoast):

make a script called mailip.sh in ~/bin, as done for the other scripts above.  Paste in the following data, modifiying it with your email info:

```

#!/bin/bash
NEWIP=`/home/YOUR_USER_NAME/bin/get_wanip.sh`
if [ `cat /home/YOUR_USER_NAME/.wanip/prev_ip` != "$NEWIP" ] ; then
echo "New IP address is $NEWIP"
echo $NEWIP > /home/YOUR_USER_NAME/.wanip/prev_ip
cat /home/YOUR_USER_NAME/.wanip/prev_ip | sendEmail -f [email]YOUR_EMAIL_NAME@YOUR_PROVIDER.COM[/email] \
-t [email]YOUR_FAVOURITE_EMAIL@WHEREVER.COM[/email] \
-s MAIL.YOUR_PROVIDER.COM \
-u "New IP $NEWIP" \
-m "$NEWIP"
fi

```

install the program that you need to send the email, and make the script executable:

```

chmod +x ~/bin/mailip.sh
sudo apt-get install sendemail

```

Now add this script to Kcron as done for send_wanip.sh above.

Finally, make sure your router is forwarding the ports of interest to your computer, and that your firewall is letting them through as well.  I personally use firestarter, so I added a policy for port 22 (ssh) to allow incoming connections, and also forwarded the port to my local IP from the router.  You will have to see the instructions for your router to learn how to do this.

To login to your computer from any remote location, type into any terminal:
```

ssh YOUR_USERNAME@295.123.52.23 (use your ip here, this one is made-up)

```
(this also works from a windows machine with PuTTy).  You can also log in over an sftp connection, it uses the same port 22 and has nice GUI interfaces such as gFTP or filezilla.

Good Luck!

---

### Post by T*&amp;1p87)v# on 2006-04-05
I personally use Dynamic DNS to keep track of my dynamic ip. It is much less work for me. 
But your idea looks very nice, and also cool, haven't tried it because I could not get smssend send sms to my phone. I am using O2-DE provider.

Nice work though :-D

---

### Post by pestilence4hr on 2006-04-05
Not to rain on your parade, but there already is a pretty decent solution to this problem in dyndns.org.  Using ddclient, you have your machine automatically update a free hostname that you can choose.  You might want to check it out, it will save you a bundle in sms messages :)

---

### Post by Jason_25 on 2006-04-05
I'm on dyndns as well and the settings are built into my router. Very convenient.

---

### Post by Nano on 2006-04-06
Indeed, my router even has built-in dyndns support.

---

### Post by cstudent on 2006-04-06
[www.no-ip.com](www.no-ip.com) has a linux script that pretty much does the same thing too.

---

### Post by zachtib on 2006-04-06
My solution is even easier: I have a static ip address :P
Though I may try something like this for the actual computers in my house, as only my webserver has a static ip inside our network...

---

### Post by pestilence4hr on 2006-04-06
[QUOTE=zachtib]My solution is even easier: I have a static ip address :P
Though I may try something like this for the actual computers in my house, as only my webserver has a static ip inside our network...[/QUOTE]

Wouldn't it be easier to just configure your dhcp server inside your house to give the same ip to your computers?  The only reason for using dyndns is when you have no control over the ip assignment.

---

### Post by zachtib on 2006-04-06
[QUOTE=pestilence4hr]Wouldn't it be easier to just configure your dhcp server inside your house to give the same ip to your computers?  The only reason for using dyndns is when you have no control over the ip assignment.[/QUOTE]

probably, but there are a couple of XP home computers, a mac, and several linux boxes on this network, also laptops that move around a lot, and all I care about are the addresses of a few of my pc's, so ill just have it message/email me the addresses for those

---

### Post by SqRt7744 on 2006-04-07
That's nice, but for me sms messages are free.  But thanks for the heads up!

---

### Post by asdlkf on 2006-04-15
It would be easier yo pull the ip address from [www.whatismyip.ORG](www.whatismyip.ORG) rather then [www.whatismyip.com](www.whatismyip.com). none of the string manipulation BS.

---

### Post by SqRt7744 on 2006-05-11
Wow, that's awesome!  I can't believe I didn't notice that.  Ah well...

---

### Post by nmhitman on 2006-05-15
I'm wondering how I might go about modifying the script to instead send the new ip in an email.  Unfortunately I use US Cellular as a carrier and they don't have a *.sms file available, not to mention text messages cost $ whereas email is free; and anywhere that I might need to ssh into home must have a valid internet connection to do so, thereby allowing me to check my email.

Also, is there anyway to write these scripts in C, or java?  Or would you recommend picking up a new language (PERL or Python??) for script writing?

Thank you in advance for your time and input; it is greatly appreciated.  I have found the community to be more than helpful in transitioning to linux over the last several months.

---

### Post by SqRt7744 on 2006-05-16
hrm!  Well perhaps it would be worthwhile in your situation to use they dyndns suggestion of some of the earlier posters, setting it up is described on easylinux.info in the dapper section.  

It is certainly possible to have your IP emailed to you, but I'm not sure a.t.m. how I'd go about doing it... if I'm not mistaken it is a somewhat more involved process.

Also, you certainly could write this script in C or Python or whatever language makes you happiest, however I have chosen to keep it simple and use shell scripting.  If I may recommend a language to you and it must be either Perl or Python, I'd choose python.  Just a personal bias however, I'm not trying to start any flame wars.

---

### Post by magictoast on 2006-05-31
I had a similar problem.  I have a linux box I use for stripping info out of .CDR files and stuff with some small scripts I've written.  Problem was, whenever it was rebooted, it was assigned a newip via DHCP.  So I wrote this VERY crude script below, to email me my new IP address.  Just save it in a text file and chmod +x filename.  Then it can be added to your startup routine, or a cronjob.


#!/bin/bash
NEWIP=`ifconfig | grep 192.168`
if [ 'cat /home/timmay/iplogfile' != "$NEWIP" ] ; then
echo "studnix - new IP address is $NEWIP"
echo $NEWIP > /home/timmay/iplogfile
cat /home/timmay/iplogfile | sendEmail -f [email]my.name@somesite.ca[/email] \
                                  -t [email]me@somesite.ca[/email] \
                                  -s postoffice.somesite.ca \
                                  -u "New IP For studnix!"
fi


Like I said, it's crude, but it works.

---

### Post by SqRt7744 on 2006-06-01
[QUOTE=magictoast]I had a similar problem.  I have a linux box I use for stripping info out of .CDR files and stuff with some small scripts I've written.  Problem was, whenever it was rebooted, it was assigned a newip via DHCP.  So I wrote this VERY crude script below, to email me my new IP address.  Just save it in a text file and chmod +x filename.  Then it can be added to your startup routine, or a cronjob.
[/QUOTE]

That is great, thanks!  Came at a rather opportune time too, since smssend just broke for some reason, I think Telus changed their page around.  To those out there who want to try this, first be sure to:

apt-get install sendemail

also, I made some changes to the script so that it uses the scripts I already wrote (if you followed the howto) and emails your wan ip rather than the local ip assigned to your computer by your router:

here's my version:

```

#!/bin/bash
NEWIP=`/home/YOUR_USER_NAME/bin/get_wanip.sh`
if [ `cat /home/YOUR_USER_NAME/.wanip/prev_ip` != "$NEWIP" ] ; then
echo "New IP address is $NEWIP"
echo $NEWIP > /home/YOUR_USER_NAME/.wanip/prev_ip
cat /home/YOUR_USER_NAME/.wanip/prev_ip | sendEmail -f [email]YOUR_EMAIL_NAME@YOUR_PROVIDER.COM[/email] \
-t [email]YOUR_FAVOURITE_EMAIL@WHEREVER.COM[/email] \
-s MAIL.YOUR_PROVIDER.COM \
-u "New IP $NEWIP" \
-m "$NEWIP"
fi

```

be sure to replace your all the emphasized usernames/email addresses with your info.

---

### Post by SqRt7744 on 2006-06-01
just a quick note:

[QUOTE=magictoast]
if [ 'cat /home/timmay/iplogfile' != "$NEWIP" ] ; then
[/QUOTE]

has the wrong single quotes.  It should actually read:

if [ `cat /home/timmay/iplogfile` != "$NEWIP" ] ; then

---

### Post by nrayever on 2006-06-01
ooh men this is cool!! for me too sms are for free, but i don't know if smssend works with my cell phone company. i should look for it. might sound pretty stupid, but is a great solution. the one with email, it's cool too!! i hope to see more scripts like this. thanks a lot!

sincerly nrayever

---

