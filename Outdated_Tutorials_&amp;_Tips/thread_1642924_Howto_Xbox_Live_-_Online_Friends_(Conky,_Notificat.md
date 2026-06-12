---
title: "Howto: Xbox Live - Online Friends (Conky, Notification Area, Etc)"
date: 2010-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by kingbilly on 2010-12-11
This script fetches your Xbox Live friend list - Gamertags and activity, removes offline Gamertags, and finally encloses them in XML tags making it easy for you to further export/customize them.

[SIZE="1"]This script was created as a replacement for the one in [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7761287#post7761287") which became incompatible when Microsoft changed the main content xbox.com friend pages to load with javascript.  Instead of xbox.com we now use bungie.net

[COLOR="DarkRed"]Known Issues:[/COLOR]
Just like the outdated script, there is still the inconvenience of having to export cookies daily.  Hopefully someone who finds this useful is also an expert with cookies and sessions.

Here is a screenshot of the final product, customized for Conky.
[[IMG]http://ompldr.org/tNmlqNA[/IMG]]("http://ompldr.org/vNmlqNA")
Now let's begin![/SIZE]

[SIZE="4"]Prerequisites[/SIZE]

**wget** - Most distributions have it by default.  But if you are running on a server install for some reason there is a chance you could be missing it (Is it Debian Server that is missing it?).

**Working Directory** The script works best if everything is in the same directory (Cookie file, actual script).  This is especially useful if your method of automation (cron, conky, etc) makes things funky.
[COLOR="Red"]By default, this script changes directory to ~/.xbl_friends[/COLOR]
If you don't mind seeing it in your home folder, change the script to non-hidden location since it will be easier to put the new cookie file in daily.  If your advanced, just do what you want.  But the further away from hardcoded paths, the tougher it will be to troubleshoot.

**Cookies**
You need to have a cookie file for WGET to use each time it connects.
1) I use Firefox for this.  If you can not use Firefox you will have to figure out your own solution for these steps.  The latest Firefox versions keep cookies in database instead of a text file.  To get what we need we will [COLOR="blue"][This Firefox Extention]("https://addons.mozilla.org/en-US/firefox/addon/8154/")[/COLOR].
2) Once installed, visit bungie.net and sign in, [COLOR="DarkRed"]making sure you check "Save my Login and Password"[/COLOR].  After you have signed in, click Tools in Firefox and choose the new option "Export Cookies"  Save the file in ~/.xbl_friends (or where you edit the script to look) and name file cookies.txt and click export.

[SIZE="5"]The Script[/SIZE]
Make a new file in ~/.xbl_friends (once again, or wherever) and name is whatever you want (I chose xbl.sh).
Then paste the following code inside
```
#!/bin/bash
#
# Xbox Live Friends List 0.3 - Slightly Less Ugly Edition (how do I program?)
# Feedback: kingbilly @ ubuntuforums
# 
# I put this line in because I don't understand cron and working directories.
# It is recommended that you force the script to intentionally use a directory.
# Comment this line out if you have different intentions.
cd $HOME/.xbl_friends
#
# Remove existing files so WGET won't create names with prepended numbers each time the script is run
rm ./friends.aspx
#
# The language between Firefox Export Cookies(depending on method) and Weget Load Cookies is different, this takes the guesswork out
# Preventing the script to fail over one tiny letter ( "s" ).
# This line stays in the script since exporting cookies must happen daily until a workaround if found.
if [ -e cookie.txt ];
then
mv cookie.txt cookies.txt
fi
#
# Download file from website
wget --load-cookies=cookies.txt --keep-session-cookies --ignore-length --no-check-certificate --output-document friends.aspx https://www.bungie.net/Stats/LiveFriends.aspx
#
# Create list of Gamertags 
cat friends.aspx | grep '<li class="name">' | sed 's/\x0D$//' | sed -e 's/<li class="name">/<tag>/g' | sed -e 's/<\/li>/<\/tag>/g' | sed '/^$/d' | tr -d ' '  > online_friends.xml
#
# Create list of current activities
cat friends.aspx | grep -A 2 '<li class="game">' | sed 's/\x0D$//' | sed -n '/&nbsp;/p' | sed 's/&nbsp;/<act>/g' | sed 's/^[ \t]*//;s/[ \t]*$//' | sed 's/$/<\/act>/g' > online_status.xml
#
# Join two files side by side, which matches each Gamertag with the Activity.
# Remove offline Gamertags.
# Remove tab character that is a result of the paste command.
paste online_friends.xml online_status.xml | tr -d '\011' | sed '/Offline/ d' > online_friends_status.xml

exit
```

Run the command from the terminal to test it.
```
cd ~/.xbl_friends
sh xbl.sh
```
You will see the wget command being executed.

There will now be two additional files in your .xbl_friends folder.
```
richard@rich-hp-ubuntu:~/.xbl_friends$ ls
cookies.txt  friends.aspx  online_friends_status.xml  xbl.sh

``` 
The xml file will have tags around the data inside ```
<tag>Gamertag</tag> and <act>Activity</act>.
```
This makes it easy for anyone to remix the information for their own needs.  But maybe you just want this in Conky without the XML tags?
Simply add this code to the script, on the second to last line (before exit)
```
cat online_friends_status.xml | sed 's/<tag>//g' | sed 's/<\/tag>//g' | sed 's/<act>/ - /g' | sed 's/<\/act>//g' > online_conky.xml
```

Now you can just have Conky read the contents of online_conky.xml.

[SIZE="5"]Tips[/SIZE]
[SIZE="3"]Conky[/SIZE]
To have Conky display the contents of online_conky.xml, add this to your running conkyrc file:
```
${execi 300 cat ~/.xbl_friends/online_conky.xml}
```
Which will have Conky refresh this file every 5 minutes.  Of course, the Xbox Live Friends script needs run every 5-10 minutes to make this relevant.

Also, since I only own a few games I have my copy of the script change the color of each Gamertag and Activity that matches a game I have.  This way I notice it faster on my desktop that I have an opportunity to play with a friend.  Here is an example:
```
cat online_friends_status.xml | sed 's/<tag>//g' | sed 's/<\/tag>//g' | sed 's/<act>/ - /g' | sed 's/<\/act>//g' | sed 's/Halo: Reach/${color white}Halo: Reach${color green}/g' > online_conky.xml
```
This makes the entire left-to-right line turn white (as opposed to green, which is how Conky displays for me if you check the above screenshot).
Note: For this type of example you will have to change the execi command in Conky to exec**p**i so that it parses the ${color] statement.
```
${[COLOR="Black"]**execpi**[/COLOR] 300 cat ~/.xbl_friends/online_conky.xml}
```

[SIZE="4"]Automation[/SIZE]
I prefer to use cron for automating this script.
```
crontab -e
```
You are welcome to use your own preferred method, but keep this in mind;
When I first made the script and used cron I had this:
```
0-59/10 * * * * /home/richard/.xbl_friends/new.sh
```
But that didn't work.  Checking the system log files I was able to see some error messages.  Adding **/bin/bash** to the cron table however made them go away, and made the script work
```
0-59/10 * * * * /bin/bash /home/richard/.xbl_friends/new.sh
```
So the point is make sure that your method for automating the script is something you understand, and can control.

[SIZE="5"]Future Versions[/SIZE]
I plan to update the script to offer a few more features.

1) Show offline friends if they have only been offline for a few minutes.

2) Utilize the notification system (At least on Gnome where I currently am) to show when someone a friend appears online.

3)  I am not the right person for this job - If someone can figure out how cookies work maybe we can fix the issue of having to export the cookies every day.  If you browse with Firefox/Chrome every day you don't have to login.   So why does wget lose the privilege every 24 hours?

Eveyone is welcome to assist with these future items.  Maybe someone knows how to make these show up in Pidgin or other buddy lists.

---

### Post by fooey on 2010-12-14
nice write up man. thx. that's a lot of damn work for just some xbox online statuses, but it's still cool to see interesting ways to display info on your desktop like this


btw, don't forget to feed your cats! ;)

---

### Post by kingbilly on 2010-12-22
Thanks. The cat says thanks too :p

---

### Post by djyoung4 on 2011-01-11
would there be a way to display just the top five friends if they are on xbox live or not like the old one did.  This wont be at the bottom of my conky so when more people come on it will shift my conky's placement all over the place.  any ideas?

---

### Post by kingbilly on 2011-01-22
> **djyoung4 said:**
> would there be a way to display just the top five friends if they are on xbox live or not like the old one did.  This wont be at the bottom of my conky so when more people come on it will shift my conky's placement all over the place.  any ideas?

Yes :D , change the second to last line:

```
paste online_friends.xml online_status.xml | tr -d '\011' | sed '/Offline/ d' > online_friends_status.xml
```

into this:

```
paste online_friends.xml online_status.xml | tr -d '\011' | sed '/Offline/ d' | head -n 5 > online_friends_status.xml
```

The head -n command will truncate the lines after the number you enter, in this case 5.

:p

---

### Post by ironic.demise on 2011-02-05
Firstly, the cookies thing.
Whenever you visit the site, a browser automatically "redownloads" the cookie anyway iirc... so basically, this does the same thing anyway.

Would it be reasonable to use an indefinite while loop to get this to repeat and have a "live" feed (excuse the pun)?

Using a while loop would refresh the cookie and the contact list without needing to re-run the script... Maybe you could time the while a bit using a variable based on the seconds, so if seconds were every minute or so?

Definite subscribe, interested and although I don't use wget, I'm certainly thinking about it.

---

### Post by kingbilly on 2011-02-06
> **ironic.demise said:**
> Firstly, the cookies thing.
Whenever you visit the site, a browser automatically "redownloads" the cookie anyway iirc... so basically, this does the same thing anyway.

Would it be reasonable to use an indefinite while loop to get this to repeat and have a "live" feed (excuse the pun)?

Using a while loop would refresh the cookie and the contact list without needing to re-run the script... Maybe you could time the while a bit using a variable based on the seconds, so if seconds were every minute or so?

Definite subscribe, interested and although I don't use wget, I'm certainly thinking about it.
I thought that was what happens, but after 24 hours wget no longer had a valid session which caused the script to halt.  Hence the exporting of cookies that otherwise seem to update each time in Chrome/Firefox/IE and such.  

Of course I really don't know much about this, I simply picked up the pieces of a previous work and made it compatible after Microsoft redesigned their Xbox Live website.

If you think you can figure out a way to make this better starting with the cookies, take a stab at it.  Or tell me what to test.  I also don't understand programing far enough to make a "while" statement. So if you cook something up for that show me. ):P

Thanks for the interest and I hope you can help make this more useful.  I dislike having to redo the process every 24 hours :lolflag:

---

### Post by ironic.demise on 2011-02-06
This is just a bit of a guess, I've done while loops before and though I know this isn't the "correct" method of doing it.

```
#! /bin/bash
[b]
VARIABLE=0
while [ $VARIABLE = 0 ]
do[/b]
[i]rest of script after #! /bin/bash
but don't include the exit command[/i]
**done**
*exit 0*
```
Variable will (or should) never be any different to 0
Variable can be anything, a=0 b=0... Just so long as the variable in while matches.
I'm sure you can use words too, like VAR=ONE... but it's made more sense to me to use a number.

If you use while [ $? = 0 ] then it will only leave if it errors... but I don't see the point in that and I don't think it's reliable.

:edit: This *should* get the cookie over and over again.
Oh, wait, firefox get's it... I don't know if there's a way to get the cookie any other way, maybe using wget with a password? ```
wget -u name:pass
```

---

### Post by djyoung4 on 2011-04-02
has there been any progress on this

---

### Post by kingbilly on 2011-04-21
> **djyoung4 said:**
> has there been any progress on this

I've been mega busy with work and installing Ubuntu on laptops for people (i'm not even pushing it, they come to me!)

But take a look at the work in my old thread:
 [http://ubuntuforums.org/showpost.php?p=10606575&postcount=12]("http://ubuntuforums.org/showpost.php?p=10606575&postcount=12")

I will contact the author about merging into the OP of this how-to thread when I get the chance.

---

