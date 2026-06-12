---
title: "Add right-click virus scanning capability to Nautilus"
date: 2005-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by robert_pectol on 2005-12-15
With this script saved in ~/.gnome2/nautilus-scripts, you can scan files or directories for viruses by simply right-clicking on them in Nautilus and selecting this script from the, "Scripts" dropdown menu. It relies on Clam Anti-virus which can be easily installed by doing, "sudo apt-get install clamav" in a shell. Simply copy the code below, into a text file and save it as, "virus-scan" and make it executable (ex: chmod 755 virus-scan). Again, it needs to be located in your ~/.gnome2/nautilus-scripts (dot in front of 'gnome2') directory. Anyway, here's the script:

```

#!/bin/bash
#
#  Nautilus anti-virus scanner script v1.2 - Uses Clam Anti-virus
#  Written by Robert Pectol, December 2005 - http://rob.pectol.com
#
#  This program is free software.  It is distributed in the hope
#  that it will be useful, but WITHOUT ANY WARRANTY; without even
#  the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR
#  PURPOSE.  See the GNU General Public License for more details.
######################################################################

#  Set some variables used in the script
files=$1
if [ "$NAUTILUS_SCRIPT_CURRENT_URI" == "x-nautilus-desktop:///" ]; then
        files_path=$HOME"/Desktop"
else
        files_path=`echo $NAUTILUS_SCRIPT_CURRENT_URI | sed -e 's/^file:\/\///'`
fi
gui=`which zenity`
vscan=`which clamscan`

#  Function to scan file(s)
scan_it()
{
        touch /tmp/scanresult
        if [ "$files_path" = "" ]; then
                #  Script can run from launchers, scripts other than from Nautilus, etc. (doesn't require $NAUTILUS_SCRIPT_CURRENT_URI)
                result=`$vscan -r "$files" --log=/tmp/scanresult | $gui --title "Virus Scanner" --progress \
                --text="Scanning $files..." --pulsate --auto-close; cat /tmp/scanresult` &> /dev/null
        else
                result=`$vscan -r "$files_path/$files" --log=/tmp/scanresult | $gui --title "Virus Scanner" --progress \
                --text="Scanning $files..." --pulsate --auto-close; cat /tmp/scanresult` &> /dev/null
        fi
        rm -f /tmp/scanresult &> /dev/null
        #  Feedback - if scan ended with errors or was terminated prematurely...
        if [ "$result" = "" ]; then
                err_text="Virus scan on $files terminated!"
                errors
        fi
        #  Feedback - if scan completed successfully...
        clean=`echo $result | grep 'FOUND'`
        #  Alter gui feedback according to presense/absense of virus(s) found during scan
        if [ "$clean" != "" ]; then
                $gui  --title "Virus Found!" --error --text="$result" &> /dev/null
        else
                $gui  --title "Virus Scan Results!" --info --text="$result" & &> /dev/null
        fi
}
#  Function to handle errors
errors()
{
        $gui  --title "Virus Scan Error!" --error --text="$err_text" &> /dev/null
        exit 1
}

#  Check for presense of required utilities
if [[ -x "$vscan" && -x "$gui" ]]; then
        scan_it
else
        if [ -x "$vscan" ]; then
                echo "Zenity was NOT found on the system!"
                exit 1
        else
                err_text="Clam Anti-virus was NOT found on the system!"
                errors
        fi
fi
exit 0

``` 
Enjoy!

---

### Post by robert_pectol on 2005-12-17
**Deleted!**
I edited the original post to include the info contained in this one!  :)

---

### Post by ceti on 2005-12-17
Good, thanks!
It works even for folders.

---

### Post by robert_pectol on 2005-12-17
You're welcome!  I'm also working on a file encrypter/decrypter script for Nautilus.  It uses GnuPG.  If there's any interest in such a script, let me know and I'll dedicate some more time to it to get it done sooner.

---

### Post by Rob2687 on 2005-12-17
It gives and error...

'Error: Can't access' what ever file/folder I'm trying to scan

edit: It only does that when scanning files on the desktop.

---

### Post by Bloot on 2005-12-17
[QUOTE=Rob2687]It gives and error...

'Error: Can't access' what ever file/folder I'm trying to scan

edit: It only does that when scanning files on the desktop.[/QUOTE]

Yep, appart from that issue it works like a charm.

Thanks for the howto.

---

### Post by ceti on 2005-12-17
[quote=robert_pectol]You're welcome! I'm also working on a file encrypter/decrypter script for Nautilus. It uses GnuPG. If there's any interest in such a script, let me know and I'll dedicate some more time to it to get it done sooner.[/quote]

C'mon, let's see it....

---

### Post by robert_pectol on 2005-12-17
Thanks for letting me know. It was a minor bug and I've addressed it with this new version. It seems to have been an issue with the script knowing the full path to the directories/files to be scanned, and getting that info from Nautilus. So, I've made a couple of changes to the script to do that. I've tested it here locally and so far, it appears to be fixed. Give it a try and let me know. If you can break it, I'd like to hear about it. That's how these things get ironed out! I've replaced the script on the original posting with the updated version. If the script didn't get pasted properly or you'd like to download it directly, it is available here:
[http://rob.pectol.com/myscripts/vscan.sh.txt]("http://rob.pectol.com/myscripts/vscan.sh.txt")

---

### Post by dcstar on 2005-12-17
Good stuff, thanks for doing it!

---

### Post by bscbrit on 2005-12-17
Rob.  Thank you. 

Having looked at the code I realise that I could probably have written it myself - but I didn't and you did!  Good effort.  (perhaps I might even try some of my own)

---

### Post by robert_pectol on 2005-12-18
You're welcome!

---

### Post by Bloot on 2005-12-18
Thanks for fixing the bug!

---

### Post by Danielle on 2005-12-18
thanks for the script, robert :D can't you just edit your first script from post#1 so it works? i ended up having to save it twice, not that i care, it might have taken me abit longer to write the script :razz: 

it's really good thanks.

---

### Post by Danielle on 2005-12-19
[QUOTE=robert_pectol]I'm also working on a file encrypter/decrypter script for Nautilus.  It uses GnuPG.  If there's any interest in such a script, let me know and I'll dedicate some more time to it to get it done sooner.[/QUOTE]
i think it would be perfect. does it use a strong algorithm? it's not important i can't see my Mum taking an interest in breaking encryption keys. i still have to do her emails :rolleyes:

---

### Post by robert_pectol on 2005-12-19
In regards to my mentioning of a file encrypter/decrypted script for Nautilus which I've been working on...

[quote=Danielle]i think it would be perfect. does it use a strong algorithm? it's not important i can't see my Mum taking an interest in breaking encryption keys. i still have to do her emails :rolleyes:[/quote]

Yes!  It uses GnuPG.  See their Website for more info:
[http://www.gnupg.org/(en)/features.html](http://www.gnupg.org/(en)/features.html)

The script is about finished but I'm holding off from posting it until I can have a chance to fully debug it.  I'll post it to a new thread when I release it.

I'm glad you like my virus scanning script!  By the way, I have removed the original script from the first posting.  Initially, I chose to leave it intact for the sake of thread continuity but I'd rather be certain that folks have the fixed version. ;)

---

### Post by robert_pectol on 2005-12-26
Ok... I've posted my file encrypter/decrypter script for Nautilus so it should show up in the forum sometime soon.  However, for the truly impatient, it can be downloaded here:
[http://rob.pectol.com/myscripts/encryption.sh.txt]("http://rob.pectol.com/myscripts/encryption.sh.txt")

Enjoy!

---

### Post by viscount on 2005-12-26
Thanks Rob,
Just found these, looks pretty good!

---

### Post by honeydew on 2005-12-28
[QUOTE=robert_pectol]You're welcome!  I'm also working on a file encrypter/decrypter script for Nautilus.  It uses GnuPG.  If there's any interest in such a script, let me know and I'll dedicate some more time to it to get it done sooner.[/QUOTE]

yes please!

---

### Post by anil_robo on 2005-12-28
Tested and proven!
Click on the thumbnail to see! :)
[ATTACH]4867[/ATTACH]

---

### Post by Gooks on 2005-12-28
How do i install this??? How do i get it in gnome2??

---

### Post by smack on 2005-12-28
[QUOTE=Gooks]How do i install this??? How do i get it in gnome2??[/QUOTE]

In your home directory you have dot files that are hidden. If you open up your home directory in nautilus and hit ctrl-H it'll show you the files.

You pretty much have to save his script in a text file. I called mine clamavscan.

You just copy that text file you make in to the directory he specified, the hidden one with the '.' in front of it.

The last thing you'd have to do is right click that script file and go to properties/permissions and make it executable.



robert_pectol: I dig this script man! This will be nice to run before I share files to my windows friends at lanparties and what not. I added you to my forum buddly list. :)

---

### Post by Gooks on 2005-12-28
How do i make it save in that DIR?

---

### Post by smack on 2005-12-28
[QUOTE=Gooks]How do i make it save in that DIR?[/QUOTE]

If you were using gedit it'd ask you for a save location when you save a new file. You could also just save the text file on the desktop and drag it to the right place.

---

### Post by daibak on 2005-12-29
Congrats to Robert Pectol for this handy little right-click menu tool in Nautilus I'd been missing since Windows.
ClamAV runs slow compared to what I've been used to but that's no criticism of you, I'm sure it's the folks who coded the ClamAV scan engine.
When I Save As your script in gedit, choosing Home directory, it got buried in /root and had to do a GNOME Search for Files... to find it and copy it over to the proper place in my ~/.gnome2/nautilus-scripts directory.
Perhaps someone can teach me what I did wrong so this won't confuse others.

It's guys like Robert that make Linux inebriating to newbies. Happy New Year all!

---

### Post by rjwood on 2005-12-29
Thanks a bunch! I don't get worried much about virus problems with linux-but hey-you never know-better safe then sorry!;)

---

### Post by rjwood on 2005-12-29
[quote=daibak]Congrats to Robert Pectol for this handy little right-click menu tool in Nautilus I'd been missing since Windows.
ClamAV runs slow compared to what I've been used to but that's no criticism of you, I'm sure it's the folks who coded the ClamAV scan engine.
When I Save As your script in gedit, choosing Home directory, it got buried in /root and had to do a GNOME Search for Files... to find it and copy it over to the proper place in my ~/.gnome2/nautilus-scripts directory.
Perhaps someone can teach me what I did wrong so this won't confuse others.

It's guys like Robert that make Linux inebriating to newbies. Happy New Year all![/quote]

I am new myself but, I am learning. You could have made the script in your home directory and then moved it to the proper directory, or you could have cd directories first and then opened gedit and done it all there. Either way is fine. Knowing the people on this forum though, there may possibly be some space-age way of doing it but, that's why I'm here--so I can learn from them.:p

---

### Post by daibak on 2005-12-29
[QUOTE=rjwood]... You could have made the script in your home directory and then moved it to the proper directory, or you could have cd directories first and then opened gedit and done it all there. Either...[/QUOTE]

I've learnt my lesson, thanks to rjwood. I should have learned this by now!

```
username@ubuntu:~$ cd ~/.gnome2/nautilus-scripts
username@ubuntu:~/.gnome2/nautilus-scripts$ gedit
username@ubuntu:~/.gnome2/nautilus-scripts$ ls -a
.  ..  clamavscan  testerTOsaveas
username@ubuntu:~/.gnome2/nautilus-scripts$ rm testerTOsaveas
username@ubuntu:~/.gnome2/nautilus-scripts$ ls -a
.  ..  clamavscan
username@ubuntu:~/.gnome2/nautilus-scripts$ cd ~
username@ubuntu:~$

```

To any other newbie out there, as I'd already saved Pectols' script properly as 'clamavscan' in the correct directory this was just a test to do things properly. That's why I deleted empty 'testerTOsaveas' gedit file same folder.

---

### Post by robert_pectol on 2005-12-29
Hi guys. Thanks for the kind words! Probably the easiest way to get the script downloaded and saved to the right location is to do the following:

1. First, to get to the correct location, open a shell and type, "cd ~/.gnome2/nautilus-scripts"
2. Next, to download the script, type, "wget http://rob.pectol.com/myscripts/vscan.sh.txt"
3. Then, to rename it to your liking, type, "mv ./vscan.sh.txt ./vscan.sh" (or whatever you want to call it)
4. And finally, to make the script executable, type, "chmod 755 ./vscan.sh" (or whatever you named it in step 3)

That's it!  No having to open it up in an editor at all!  ;)

---

### Post by installer on 2006-01-02
[QUOTE=robert_pectol]With this script saved in ~/gnome2/nautilus-scripts, you can scan files or directories for viruses by simply right-clicking on them in Nautilus and selecting this script from the, "Scripts" dropdown menu. It relies on Clam Anti-virus which can be easily installed by doing, "sudo apt-get install clamav" in a shell. Simply copy the code below, into a text file and save it as, "virus-scan" and make it executable (ex: chmod 755 virus-scan). Again, it needs to be located in your ~/gnome2/nautilus-scripts directory. Anyway, here's the script:

[COLOR=Red][/COLOR]```

**Removed!**  Please use the updated one listed a few posts below!

``` 
Enjoy![/QUOTE]


Excellent, thank you. :p

---

### Post by robert_pectol on 2006-01-05
You're welcome! :)

---

### Post by Gray. on 2006-01-05
Thanks for the script, very handy.

---

### Post by faizan on 2006-01-06
thanks for this robbie.. peaceful and handy!

---

### Post by Pretzal on 2006-01-06
nice script... Newbies like me really appreciate this kind of stuff. Thanks

---

### Post by robert_pectol on 2006-01-07
I'm glad you all found it useful!  Thanks for letting me know.

---

### Post by ifyc576 on 2009-03-21
Thank you for the script.  It worked fine.

I have one question; can you select more than one file to scan at a time?  I'm only able to scan one file at a time, when I select multiple files ClamAV seems to ignore anything past the first file.

Thanks Again!

---

### Post by karthick87 on 2010-02-11
Where is the updated version of this script???When i run this script i get an error how to fix it??

---

