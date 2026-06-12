---
title: "XBOX360 Friends List on Conky"
date: 2009-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by LostDakota on 2009-08-10
So I have been trying to find a script or some other tutorial on how to get my XBOX360 friends list to display in conky. Being unsucessfull, I decided to try my hand at creating one of my own. Now before you go off on me about how messy or bloated this is, or how much MS sucks, please note that I have only been using ubuntu for 6 months in my spare time and 360 is still pretty cool(IMO.) So if you have suggestions on how I can be more efficient, I'd love to hear them. As it stands, there are some flaws. Which is why I'm posting this so that those who are more educated can help me perfect it. And so it goes.

CONKY XBO360 FRIENDS LIST

1.) I use Firefox. I like it. If you use something else, I have no way to help you other than the usual "Google it!" So, we need a way to get the cookies from Firefox. FF has begun using cookies.sqlite instead of cookies.txt (which we need.) So the first step is to download a handy FF extension that does the conversion for us. [Clicky. ]("https://addons.mozilla.org/en-US/firefox/addon/8154")

2.) Once installed, visit [xbox.com]("http://www.xbox.com") and sign in making sure to check "Save my Login and Password." After you are signed in, click Tools in FF and you will notice the option "Export Cookies..." Click on it and a dialog box will come up asking you to name it and where you want it to go. The default (at least for me) was cookies.txt and the dir ~/ I left it like that and clicked Export. 

3.) The reason for all the cookie business is that wget need them to get past the M$ Javascript Login. We have to use wget to save the html of the Friends page. You do this by entering this into a terminal.

```
wget --load-cookies=cookies.txt --keep-session-cookies --ignore-length --no-check-certificate http://live.xbox.com/en-US/profile/Friends.aspx
```

This will save a file called Friends.aspx to your home directory.

4.) Now comes the part where you vets will shake you head and probably start twitching. Open up gedit, pico or vi and create a script in /usr/bin named xFriends. (You can name it whatever you want really. Just remember to change it in your conky.rc file.) Here it is...

```
#!/bin/bash

rm ~/Friends.aspx

wget --load-cookies=cookies.txt --keep-session-cookies --ignore-length --no-check-certificate http://live.xbox.com/en-US/profile/Friends.aspx

cat Friends.aspx | grep 'h3\|Status' | tail -n+2 | tr -s " " " " | grep 'h3\|Xbox' | tr -s '"' "\n" | grep 'h3\|/span' | sed 's#\/span##g' | tr -s ">" " " | tr -s "<" " " | sed 's#\/h3##g' | sed 's#\h3##g' | sed 's/ |* /&|/g' | tr -s " " " " | head -n10
```

The rm removes the Friends.aspx file so it doesn't create Friends.aspx.1, etc. The wget retrieves the page again. Then the debauchery hacks the html into what I felt was relevant to display in conky. Save the script and chmod 755 it.

5.) In your conky.rc file, type this where you want the list to appear. 

```
${execi 30 /usr/bin/xFriends | head -n12}
```

And viola! Your top 5 friend (either on line or top alphabetically) will be displayed on you desktop. And updated every 30 seconds. 

Now, I leave it up to you to modify as you see fit. I have noticed, that you need to Export Cookies daily or else it poops the bed and wont work. Formatting has also been an issue for me. Help me with this if you can. If not, oh well, I tried and it suits my needs/wants. 

P.S. I tried to type all of this into the New Post form and I believe I failed miserably. So if by some stretch I have double posted, (mods) feel free to banish one or the other to /dev/null. Screen shots follow.

---

### Post by sard on 2009-09-26
Ingenious.  I just did a view source on the friends page and though how horrible it looked to parse.  I'll give your script a try!

---

### Post by kyoji on 2009-10-27
First, Thanks for the post. I can't believe there is not a team working on this!!

So this is my N00b (what I have learned in the past 2 days of shell/linux) attempt using your code as a base. 

The goal of this code is to show only the friends that are online. 

```
#!/bin/bash

Filename=~/Friends.aspx
line=`awk '/ Online/' $Filename | wc -l`   #Gets the line count to determin how many friends are on.
linect=$((line-1))      # Line will find 1 entry that does not relate to a friend, so this removes it.
FRIENDS=$((linect*2)) #used to print only friends online.

rm ~/Friends.aspx

wget --load-cookies=cookies.txt --keep-session-cookies --ignore-length --no-check-certificate http://live.xbox.com/en-US/profile/Friends.aspx ;

if [ "$line > 1" ]  ; then     

    awk '/h3|Online/' $Filename | sed -e '{
        s/<h3>//         #Deletes HTML "h3" tags.
        s/<.*>//g        #Deletes all other HTML tags.
        /Online/d        #Deletes the Online line.
        s/^ *//          #Moves txt to the right.
        s/^[^-]./*&/     #Places an "*" in front of the gamertag.
        s/^-//           #Deletes "-" in front of gamer status.
        s/[[:space:]]$// #Removes white spaces (conky writes them as a square box).   
        2d               #Deletes 2 blank lines at the beginnig of the piped txt.
	/^$/d
        }
    ' | head -n$FRIENDS ;
    
else 
    if [ "$line <= 1" ] ; then
        echo '**No Friends are online**' ;
        
    fi

fi


```

So far this works fine in a terminal, but conky will only write the first 4 friends and adds a blank line under each friend for some strange reason. Anyone got any ideas on why this is? :confused:

***Update*** I was able to fix the extra return line, but am still having problems with only 4-5 friends showing up.

---

### Post by djyoung4 on 2010-10-28
it seems Microsoft changed up there site and the script no longer works.  any updates to come to fix this.  I really like this script and would like to see it working again.  the Friends.aspx no longer shows anything in it so that could be a big problem.

---

### Post by kingbilly on 2010-11-18
So we need to figure out a way to fix this.  If anyone is good with grep, sed, awk, etc.. we could get this going again.

The new xbox live site uses all inline javascript for the new friends page, which from what I have read will not work with wget.  But individual profiles can still be accessed with wget. This wouldn't be pretty because it would require a separate wget for each friend on your list.

I am going to start a new thread in development and programming.  It shouldn't be in Tutorials & Tips until it actually works.

[http://ubuntuforums.org/showthread.php?p=10130635#post10130635]("http://ubuntuforums.org/showthread.php?p=10130635#post10130635")

---

