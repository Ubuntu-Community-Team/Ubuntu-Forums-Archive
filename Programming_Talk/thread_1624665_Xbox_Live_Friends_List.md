---
title: "Xbox Live Friends List"
date: 2010-11-18
forum: Programming Talk
---

### Post by kingbilly on 2010-11-18
[SIZE="1"]This thread is a branch of [---this---]("http://ubuntuforums.org/showthread.php?p=7761287#post7761287") that was located in Tutorials and Tips.  But it no longer contains working information, so it is time for a new solution.[/SIZE]
[SIZE="5"]
Goal[/SIZE]
The goal of this project is to create a script that can fetch the status of a user's Xbox Live friends into a usable container.  In the above referenced thread this was ideally for Conky, but there shouldn't be a limitation.  The main point is we have to clean up the garbage surrounding the relevant information. It really helps to know when your friends are online if you can't always be at the xbox/tv. ** There are desktop widgets and libnotify popups for just about everything else, but how about xbox live friends?**

[SIZE="5"]Problem[/SIZE]
Microsoft recently gave a facelift/makeover to the Xbox NXE and xbox.com.  When the change to the website took place, the easily retrievable friends list (aspx file)was removed.  It was replaced with ```
http://live.xbox.com/en-US/friendcenter?xr=shellnav
```
which neither I or anyone in the above referenced thread have been able to use wget to parse.

[SIZE="5"]Solutions[/SIZE]
#1 Someone tells us how to get wget to parse the new friends list so gamertags and statuses can be used.  This would be the easiest since it would require only one file to parse and xbox.com has more detailed information than solution #2.


#2 [COLOR="Red"]Update Nov 30th 2010:[/COLOR]
Bungie.net still have .aspx pages so it is possible to get some information from that.  But the API calls they make do not include timestamps or specific gametype/playlist/etc.  Only the gamertag and current game are called, so that is all we are stuck with.  Also, like the predecessor to this solution, cookies must be exported daily.  A fix is being looked into.

#3 The new xbox.com site has individual gamertag pages that CAN be downloaded by wget and do not require any javascript (confirmed by re-enabling NoScript for that page).  Useful information can be extracted, but it will take more work to get individual pages downloaded for every single friend, and then put all the extracted information together into one, ready to view container.  Especially since they are/have raising the friends list cap.  Imagine having 200 wget, sed, awk, and grep having to be run every 5 minutes.  

I am using the second post of this thread for Solution #2.

I welcome anyone to assist me because I have zero knowledge of sed, grep, awk, and so on :P.  If we get a working solution we can post it in Tutorials and Tips.  There are many people who can benefit from it as there is no other solution that I could find after 20 minutes of google searches.

---

### Post by kingbilly on 2010-11-18
[SIZE="5"]Solution #2[/SIZE]
[COLOR="Red"]Updated Nov 30th 2010[/COLOR]
[SIZE="1"]Currently this solution suffers from the same problem as its predecessor did - Your browser cookies have to be exported daily for this to work.  I have make a new cookie file with only the required cookies, and set them all to never expire.  I will wait 48 hours to see if this is successful. We will see if Microsoft/Bungie force the BNGAuth value to be reset daily and then overwrite all the zero's I had entered.[/SIZE]


I have realized that Bungie.net still uses the .ASPX files for serving content.  This has the benefit of only having to fetch 1-2 files.  But we loose the timestamp from xbox.com (last seen $x minutes ago).    This is still much better because in its current state xbox.com would have required a separate page download for each friend on your friends' list.  And this is after you manually enter each friend name.  I suppose we could combine these two together but for now I will just share the news about Bungie.net and aspx.

I prefer to keep my folders and desktop as clean as possible.  So if this is going to be running in the background (conky, pidgin, google gadgets, etc will be in the foreground) it might as well be hidden from file browsers.
Root Directory: ~/.xbl_friends/
Cookie File: ~/.xbl_friends/cookie.txt

Bungie.net will punch wget in the face unless you have credentials.  This was taken from the above referenced thread:
> 
1.) I use Firefox. I like it. If you use something else, I have no way to help you other than the usual "Google it!" So, we need a way to get the cookies from Firefox. FF has begun using cookies.sqlite instead of cookies.txt (which we need.) So the first step is to download a handy FF extension that does the conversion for us. Clicky.

2.) Once installed, visit [COLOR="Blue"][COLOR="Navy"]**bungie.net**[/COLOR][/COLOR] and sign in making sure to check "Save my Login and Password." After you are signed in, click Tools in FF and you will notice the option "Export Cookies..." Click on it and a dialog box will come up asking you to name it and where you want it to go. The default (at least for me) was cookies.txt and the dir ~/ I left it like that and clicked Export.

3.) The reason for all the cookie business is that wget need them to get past the M$ Javascript Login. We have to use wget to save the html of the Friends page. You do this by entering this into a terminal.


```
#!/bin/bash
#
# Xbox Live Friends List 0.2 - Ugly Edition (how do I program?)
# Feedback: kingbilly @ ubuntuforums
# 
#
#
#
#
# Remove existing files so wget won't create
# names with prepended numbers
#
#
cd ~/.xbl_friends
rm ./friends.aspx
rm ./count.aspx
# Download required files (you setup the cookies right?)
wget --load-cookies=cookie.txt --keep-session-cookies --ignore-length --no-check-certificate --output-document count.aspx https://www.bungie.net/account/profile.aspx
#
wget --load-cookies=cookie.txt --keep-session-cookies --ignore-length --no-check-certificate --output-document friends.aspx https://www.bungie.net/Stats/LiveFriends.aspx
#
# Count how many friends are online
#
online=$(cat count.aspx | grep -e '520' | grep -e 'false' | sed -e 's/430//g' | sed -e 's/520//g' | sed 's/[^0-9]//g')
#echo $online
#
#
#
cat friends.aspx | grep '<li class="name">' | sed 's/\x0D$//' | sed -e 's/<li class="name">/<tag>/g' | sed -e 's/<\/li>/<\/tag>/g' | sed '/^$/d' | tr -d ' ' | head -n$online > online_friends.xml
#
#cat friends.aspx | grep -A 3 '<li class="game">' | sed '/--/d' | sed '/</d' | sed 's/^[ \t]*//;s/[ \t]*$//' | sed '/^$/d' | sed 's/&nbsp;/<act>/g' | sed #'s/$/<\/act>/g' | head -n$online > online_status.xml
cat friends.aspx | grep -A 2 '<li class="game">' | sed 's/\x0D$//' | sed -n '/&nbsp;/p' | sed -n '/Offline/!p' | sed 's/&nbsp;/<act>/g' | sed 's/^[ \t]*//;s/[ \t]*$//' | sed 's/$/<\/act>/g' | head -n$online > online_status.xml
#
# Join two files side by side, remove tab 
# character that is a result of paste
#
paste online_friends.xml online_status.xml | tr -d '\011' > online_friends_status.xml
# My personal conky filtering
cat online_friends_status.xml | sed 's/<tag>//g' | sed 's/<\/tag>//g' | sed 's/<act>/ - /g' | sed 's/<\/act>//g' > online_conky.xml

exit
```

I renamed the profile.aspx to count.aspx but we aren't actually counting anything here.  The file has a numerical value of how many of your friends are online. [COLOR="Blue"] If anyone can figure this out from friends.aspx please let me know, it will save us a step.
[/COLOR]
The next stage of the script removes everything around the gamertags and encloses them in <tag> (short for gamertag).  This is so anyone can use some xml magic for rearranging the end data for however they see fit.  

The count of the number of friends online is used as a variable for the head command, so that only online friends are displayed.

[[IMG]http://ompldr.org/tNmRqbQ[/IMG]](http://ompldr.org/vNmRqbQ)

---

### Post by djyoung4 on 2010-12-08
thanks for lettin me know about the script.  Doesn't work for me though.  The terminal tells me this
```
home@home-desktop:~$ killall conky
home@home-desktop:~$ conky -c ~/.conkyrc4
Conky: forked to background, pid is 17563
home@home-desktop:~$ 
Conky: desktop window (14000a9) is subwindow of root window (15d)
Conky: window type - normal
Conky: drawing to created window (0x3a00001)
Conky: drawing to double buffer
/home/home/conky/conkyxbox/conkyxbox.sh: line 14: cd: /home/home/.xbl_friends: No such file or directory
Cannot open cookies file `cookie.txt': No such file or directory
--2010-12-08 14:30:40--  https://www.bungie.net/account/profile.aspx
Resolving www.bungie.net... 65.59.233.231
Connecting to www.bungie.net|65.59.233.231|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: /stats/default.aspx [following]
--2010-12-08 14:30:41--  https://www.bungie.net/stats/default.aspx
Connecting to www.bungie.net|65.59.233.231|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: ignored [application/xhtml+xml]
Saving to: `count.aspx'

    [ <=>                                   ] 33,528       214K/s   in 0.2s    

2010-12-08 14:30:41 (214 KB/s) - `count.aspx' saved [33528]

Cannot open cookies file `cookie.txt': No such file or directory
--2010-12-08 14:30:41--  https://www.bungie.net/Stats/LiveFriends.aspx
Resolving www.bungie.net... 65.59.233.231
Connecting to www.bungie.net|65.59.233.231|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: ignored [application/xhtml+xml]
Saving to: `friends.aspx'

    [ <=>                                   ] 4,219       --.-K/s   in 0.003s  

2010-12-08 14:30:41 (1.36 MB/s) - `friends.aspx' saved [4219]

head: option requires an argument -- 'n'
Try `head --help' for more information.
head: option requires an argument -- 'n'
Try `head --help' for more information.
```
it seems it the script can't find my cookies.txt file but its in ~/
any ideas?
also.  I dont know if I read right but does the script only show who is on.  Or does it show whos on plus the last few people that were on like the old script did.

---

### Post by kingbilly on 2010-12-08
The script as I posted it looks for cookies.txt inside ~/.xbl_friends

What does your .conkyrc4 contain?   I see that double /home/home I wonder what is calling it.  

I do not run the script I created with conky, because I barely understand conky. I have cron job running every ten minutes.
If you are interested run this command> crontab -e
Paste this on the last line, replacing my name with yours.
```
0-59/10 * * * * /bin/bash /home/richard/.xbl_friends/new.sh

```
Note that I named my current script new.sh

I also updated the guide, you should visit bungie.net, signin, and export cookies to be safe.  I am not sure how all that server side stuff works for them, but to play it safe visit bungie instead of xbox.

And the script only shows who is on.  At the moment the only thing I know is online, or EVERY friend.  It would be possible to color the ones actually online or mark them with a little bit of work.

I am currently working on expanding this so that the first time the script notices someone online that wasn't previously, it will use notify-osd, just like pidgin, kopete do.  But for me, I'd rather know about xbox than instant message, seems all my IM friends have migrated to facebook anyway so this would be more useful for me.  Anyway, to make this work there would be a data store of current online users to compare to future ones; so it would be possible to add what you are looking for with recently online friends.

---

### Post by djyoung4 on 2010-12-09
> **kingbilly said:**
> The script as I posted it looks for cookies.txt inside ~/.xbl_friends
does the script look for cookies.txt in there or in the folder where the script is located
> **kingbilly said:**
> What does your .conkyrc4 contain?   I see that double /home/home I wonder what is calling it.  
my conkyrc4 contains a few scripts that display my xbox friends, my music from rhythmbox, a wine script, whos on my lan and my mythtv recent and upcoming recordings
> **kingbilly said:**
> I do not run the script I created with conky, because I barely understand conky. I have cron job running every ten minutes.
If you are interested run this command
Paste this on the last line, replacing my name with yours.
```
0-59/10 * * * * /bin/bash /home/richard/.xbl_friends/new.sh

```
Note that I named my current script new.sh
I can do the conky work.  Im pretty avid in the conky community.  I just need the bash script
> **kingbilly said:**
> I also updated the guide, you should visit bungie.net, signin, and export cookies to be safe.  I am not sure how all that server side stuff works for them, but to play it safe visit bungie instead of xbox.
I saw that but still it does not work.  I get the same thing in the terminal
> **kingbilly said:**
> And the script only shows who is on.  At the moment the only thing I know is online, or EVERY friend.  It would be possible to color the ones actually online or mark them with a little bit of work.
It would be nice if microsoft didn't change there stupid site.  It used to work so nicely.  Hopefully we can get back to the old functionality
> **kingbilly said:**
> I am currently working on expanding this so that the first time the script notices someone online that wasn't previously, it will use notify-osd, just like pidgin, kopete do.  But for me, I'd rather know about xbox than instant message, seems all my IM friends have migrated to facebook anyway so this would be more useful for me.  Anyway, to make this work there would be a data store of current online users to compare to future ones; so it would be possible to add what you are looking for with recently online friends.
yeah.  that would be cool.  im just looking for the conky functionality like the old script.  I can figure out all the conky stuff.

---

### Post by kingbilly on 2010-12-09
> does the script look for cookies.txt in there or in the folder where the script is located
Okay looking out the output again i can see two of the problems.
The script expects everything to be located inside the folder ~/.xbl_friends 

You can either make that directory and put my script in there (and move cookie.txt file there too).

Or if you prefer another directory, simply edit line 14 of the script 
```
cd **~/.xbl_friends**
```
replacing the bold part with your preferred folder.

---

### Post by djyoung4 on 2010-12-09
> **kingbilly said:**
> Okay looking out the output again i can see two of the problems.
The script expects everything to be located inside the folder ~/.xbl_friends 

You can either make that directory and put my script in there (and move cookie.txt file there too).

Or if you prefer another directory, simply edit line 14 of the script 
```
cd **~/.xbl_friends**
```
replacing the bold part with your preferred folder.

editing where it is didn't work.  still got the same thing

---

### Post by kingbilly on 2010-12-09
Exact Same?  Did the 1st error at least go away?
```
/home/home/conky/conkyxbox/conkyxbox.sh: line 14: cd: /home/home/.xbl_friends: No such file or directory
```

Now about those cookies.  Did you keep your singular and plurals straight? - cookie vs cookies with the filenames and script editing.  Because a few posts ago I mistakenly mentioned cookies.txt, which is not what the script is calling during wget.

But assuming that is right, hmmm.  If you changed the directory then that is where the cookie.txt file should located.  The cd command should make everything relative to that folder.

If the error output wasn't exactly the same post it again so we can look.  



Side note, I learned the **execpi** for conky, allowing me to pass object and variables from the output of this script into something conky will parse.  So now I have mine personallized that certain games show a different color (I only own a few xbox 360 games so I want those to stand out if there is someone to play with)

---

### Post by kingbilly on 2010-12-09
On last thing before I get to bed.

When I first tried to get the script to run in cron, I had problems until I specified absolute paths AND included /bin/bash before it.
```
/bin/bash /home/richard/.xbl_friends/new.sh
```
After reading some other threads on the forums, there can be some trickery where a script works fine by itself if you run it in the terminal, but as soon as you have another program/script call it, it no longer works.


For all I know (which is nothing I tell you), Conky may be looking for cookie.txt in its own working directory.  Perhaps that is why in the previous script (before Microsoft changed their site) the creator of that script chose to put it in /usr/bin/xFriends

Hopefully some other eyes pop by this thread and help.:D

---

### Post by djyoung4 on 2010-12-24
any progress

---

### Post by kingbilly on 2010-12-25
Some progress has been made.  The latest script is on the [HowTo section ]("http://ubuntuforums.org/showthread.php?t=1642924")

There is now only one file downloaded from Bungie.net instead of two.  I was able to get all the useful info from just one.

---

### Post by swordfischer on 2011-03-27
Just to add to "solution #1",

I've been playing around, because I wanted to do some XML feeds for Xbox Live, and I've figured out a way to get the data you guys needed.

```
wget --load-cookies=cookies.txt --keep-session-cookies --ignore-length --no-check-certificate --header="X-Requested-With: XMLHttpRequest" http://live.xbox.com/en-GB/FriendCenter/friends -q -O -
```This will get you your own friendslist.

```
wget --load-cookies=cookies.txt --keep-session-cookies --ignore-length  --no-check-certificate --header=\"X-Requested-With: XMLHttpRequest\"  http://live.xbox.com/en-GB/FriendCenter/FriendsOfFriend?gamertag=GT -q -O -

```This will get you your friends, friendslist.

Enjoy, :)

--

Been playing around with conky myself.

added
```
${color grey}Xbox Live Friends
${execpi 100 cat ~/.conky/xblfriends}
```to .conkyrc

added
```
0-59/10 * * * * /home/swordfischer/xbox.com/sfdc-x360-friends-conky.pl  > /home/swordfischer/.conky/xblfriends
```to crontab

finally, my sfdc-x360-friends-conky.pl has this
```

#!/usr/bin/perl
open IN, "wget --load-cookies=cookies.txt --keep-session-cookies --ignore-length --no-check-certificate --header=\"X-Requested-With: XMLHttpRequest\" http://live.xbox.com/en-GB/FriendCenter/friends -q -O -|"or die;

my @friends_name;
my @friends_info;
my $online;
my $offline;

while(my $input = <IN>)
{
        if ($input =~ m/\<a class=\"fc-gtag-link\" href='.*'\>(.*)\<\/a>/)
        {
        push (@friends_name, $1)
        }
        if ($input =~ m/ class=\"fc-presence-text\"\>(.*)\<\/div\>/)
        {
                push (@friends_info, $1);
        }
         if ($input =~ m/\<span\>Online \((.*)\)\<\/span\>/)
        {
        $online = $1;
        }
        if ($input =~ m/\<span\>Offline \((.*)\)\<\/span\>/)
        {
        $offline = $1;
        }
}

print "\${color green}ONLINE\n\n";
for ($i = 0; $i < $online; $i++)
        {
                print "\${color white}",@friends_name[$i],"\n\t\${color lightgrey}",@friends_info[$i],"\n";
        }
print "\${color red}OFFLINE\n\n";
for ($i = $online; $i < $online+**10;** $i++)
    {
        print "\${color lightgrey}",@friends_name[$i],"\n\t\${color grey}",@friends_info[$i],"\n";
    }

```I keep my cookies in xbox.com folder, also bold number in perl script, is the number of offline friends you want to show.

[IMG]https://swordfischer.com/uploaded/conky.png[/IMG]

it is something I just threw together, and its my first time doing something in perl, any suggestions is welcome. Only thing we need is to refresh the cookie automagically

---

### Post by kingbilly on 2011-04-21
Very nice!  I like the offline friends and seeing how long ago they were on.  Going to have to try that for myself.

---

### Post by twisted_steel on 2011-04-26
I've been meaning to look into this for some time as my program (see signature) has been broken for a while after the Xbox website redesign.  The old login page used an intermediary refresh page that differs from the current one.  At the time, I just figured out what it was doing and hard-coded workarounds with ClientForm in Python.  The easiest (and most flexible) thing to do these days is probably use something along the lines of webkit and a scripting language.  Unfortunately, most implementations that I have seen use something along the lines of 50MB of RAM for just webkit.

It would be useful if there was one back-end, accessible over dbus, to let multiple programs query the friends list.  That way my program could access the information, conky scripts could access the information, and future things such as Unity integration would be possible.

---

### Post by djyoung4 on 2011-05-07
> **swordfischer said:**
> Just to add to "solution #1",

I've been playing around, because I wanted to do some XML feeds for Xbox Live, and I've figured out a way to get the data you guys needed.

```
wget --load-cookies=cookies.txt --keep-session-cookies --ignore-length --no-check-certificate --header="X-Requested-With: XMLHttpRequest" http://live.xbox.com/en-GB/FriendCenter/friends -q -O -
```This will get you your own friendslist.

```
wget --load-cookies=cookies.txt --keep-session-cookies --ignore-length  --no-check-certificate --header=\"X-Requested-With: XMLHttpRequest\"  http://live.xbox.com/en-GB/FriendCenter/FriendsOfFriend?gamertag=GT -q -O -

```This will get you your friends, friendslist.

Enjoy, :)

--

Been playing around with conky myself.

added
```
${color grey}Xbox Live Friends
${execpi 100 cat ~/.conky/xblfriends}
```to .conkyrc

added
```
0-59/10 * * * * /home/swordfischer/xbox.com/sfdc-x360-friends-conky.pl  > /home/swordfischer/.conky/xblfriends
```to crontab

finally, my sfdc-x360-friends-conky.pl has this
```

#!/usr/bin/perl
open IN, "wget --load-cookies=cookies.txt --keep-session-cookies --ignore-length --no-check-certificate --header=\"X-Requested-With: XMLHttpRequest\" http://live.xbox.com/en-GB/FriendCenter/friends -q -O -|"or die;

my @friends_name;
my @friends_info;
my $online;
my $offline;

while(my $input = <IN>)
{
        if ($input =~ m/\<a class=\"fc-gtag-link\" href='.*'\>(.*)\<\/a>/)
        {
        push (@friends_name, $1)
        }
        if ($input =~ m/ class=\"fc-presence-text\"\>(.*)\<\/div\>/)
        {
                push (@friends_info, $1);
        }
         if ($input =~ m/\<span\>Online \((.*)\)\<\/span\>/)
        {
        $online = $1;
        }
        if ($input =~ m/\<span\>Offline \((.*)\)\<\/span\>/)
        {
        $offline = $1;
        }
}

print "\${color green}ONLINE\n\n";
for ($i = 0; $i < $online; $i++)
        {
                print "\${color white}",@friends_name[$i],"\n\t\${color lightgrey}",@friends_info[$i],"\n";
        }
print "\${color red}OFFLINE\n\n";
for ($i = $online; $i < $online+**10;** $i++)
    {
        print "\${color lightgrey}",@friends_name[$i],"\n\t\${color grey}",@friends_info[$i],"\n";
    }

```I keep my cookies in xbox.com folder, also bold number in perl script, is the number of offline friends you want to show.

[IMG]https://swordfischer.com/uploaded/conky.png[/IMG]

it is something I just threw together, and its my first time doing something in perl, any suggestions is welcome. Only thing we need is to refresh the cookie automagically
anyway to only display 5-7 friends total, no matter if they are on or offlin

---

### Post by Goofball Jungle on 2011-11-07
Nice work on getting the list worikng. I would love to see A message function for xbl in there. But I'm happy as it is with this :).

---

