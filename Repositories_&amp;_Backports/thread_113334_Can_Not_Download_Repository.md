---
title: "Can Not Download Repository"
date: 2006-01-06
forum: Repositories &amp; Backports
---

### Post by Joy on 2006-01-06
Hi,
I am new to linux and computers.I have adsl router.I have installed Ubuntu version 5.10 theough install CD.I can brows. But when i go to synaptic for downloading software or Firefox 1.5 I am getting this warning-
Check your network connection and the correct writing of the Repository address in the preferances. Plus  W: Couldn't stat source package list 

[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

Please guide me.Thanks.

---

### Post by corstar on 2006-01-06
make sure you have the correct dns settings. This same problem haunted me for ages. It was such a simple fix too.
Just go to networking and then the DNS tab, then enter the dns supplied from your ISP.
That should fix it.

---

### Post by handy on 2006-01-06
I have had a similar serious problem twice when installing Ubuntu 64 & this evening the 32 bit version!

I studied wiki's & sticky's, scanned the forums until I found a solution that would have otherwise taken me a **VERY LONG TIME.**  It still took a long time to find this!

I have copied the info' here because I think it is too hard to find for those of us that need it.

Courtesy of **Python**, (though slightly modified) **I quote:**

**++++++++++++++++++++++++++++++++**

Go to MENU:--->SYSTEM ADMINISTRATION--->NETWORKING (you will need your password)

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!



Then go to /etc/resolv.conf
Make sure that these two entries are there:

nameserver 212.74.112.66
nameserver 212.74.112.67

Your ISPs nameservers replacing mine ;-P
Nameserver 192.168.blah.blah should either be commented out (preceded with a #) or not be there at all.



Finally, go to /etc/dhcp3/dhclient-script and comment out this:

# Modified for Debian. Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
# local new_resolv_conf=/etc/resolv.conf.dhclient-new
# rm -f $new_resolv_conf
#
# if [ -n "$new_domain_name" ]; then
# echo search $new_domain_name >> $new_resolv_conf
# else # keep 'old' search/domain scope
# egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# if [ -n "$new_domain_name_servers" ]; then
# for nameserver in $new_domain_name_servers; do
# echo nameserver $nameserver >>$new_resolv_conf
# done
# else # keep 'old' nameservers
# egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# chown --reference=/etc/resolv.conf $new_resolv_conf
# chmod --reference=/etc/resolv.conf $new_resolv_conf
# mv $new_resolv_conf /etc/resolv.conf
# fi
#}

That should have you sorted sunshine!

**++++++++++++++++++++++++++++++++**

**End Quote.**


Without the above I absolutely can **NOT** use Synaptic.

If this is due to my Router - Netgear DG 632, it must happen to others models too.

I believe that this info should be accessible from a Sticky.

I hope this saves someone some time.

handy

---

### Post by gfts on 2006-01-07
It seems, you are logged in as a user.

Do the following,

Go to Terminal, and type
sudo apt-get update
password : type your user password

Bingo, it should work!(hopefully)

[QUOTE=Joy]Hi,

[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
...
Please guide me.Thanks.[/QUOTE]

---

### Post by Joy on 2006-01-07
Thank you all.
I have entered ISP DNS server nos. and removed 192.168.1.1 Then where to type /etc/resolv.conf.? In terminal? with prefixing sudo  ? and finally copy &paste all commands in terminal?
Your help will be appreciated.

---

### Post by handy on 2006-01-08
Sorry.

Use the Terminal & input the following: 

**sudo gedit /etc/resolve.conf**

If **/etc/resolve.conf** doesn't exist it will be created.

Type the following into the now open gedit:

**nameserver** <your name server IP>
**nameserver** <your name server IP>

**Save**  & close gedit

See how you go with those changes.

If that works let me know, if not let me know also & we can try the next bit.

handy

---

### Post by Joy on 2006-01-09
Thank you handy. I did whate you suggested.After closing gedit i open terminal and typed sudo apt-get update and it started working.I immedediately got the update popup windows. I am sure my problem is solved.I hope now i can download firefox 1.5 and other software through synaptic package manager.
Once again thank you.
Joy.

---

### Post by Joy on 2006-01-11
Hollo, handy.
I need your help again.When I start Synaptic package manager it gave me same old warning. I checked the changes I made in sudo gedit /etc/resolve.conf as per your sugestion. There is no change.Thanks.
Joy.

---

### Post by j_baer on 2006-01-11
I performed a fresh install of breezy yesterday (01/10/2006) and in the past this has been flawless. However this time the update manager would not download the security patches.

As the other patches downloaded Ok I am assuming the issue is server/routing.

Tried again this morning and on the second attempt the updates loaded.

Just a FYI ...

---

### Post by sedgie on 2006-01-12
I updated DNS names and commented out that part of the dhclient-script.

Instead of the 404 error, I am now getting a "Temporary failure resolving "[my school's proxy server here]"

Any ideas?

---

### Post by dhungda on 2006-01-14
Hello everyone.. I'm newbie in Linux .... I have same problem... when I install Breezy I can't update/download security patch. I also have another machine with Hoary and seem running all the thing.... any suggestion?

---

