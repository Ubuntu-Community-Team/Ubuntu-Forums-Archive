---
title: "HOWTO: The Definitive Firefox &amp; Thunderbird &quot;mailto&quot; Fix"
date: 2005-03-05
forum: Outdated Tutorials &amp; Tips
---

### Post by lordofkhemenu on 2005-03-05
After a recent software update, Firefox and Thunderbird stopped working with each other. 
If Thunderbird was already open, clicking a "mailto" link (email address) resulted in the Profile Manager popping up. 
Prior to the software update(s) this wasn't an issue.
After a little googling, I found [a fix]("http://www.crazysquirrel.com/debian/firefox-mailto.php") specifically for Debian-based distros that will allow you to click on any mailto link in Firefox and have it open a new mail (including email address *and* subject line if it's part of the mailto URL) in Thunderbird whether it is running or not (if Thunderbird *is* running, you ***won't** *get the Thunderbird Profile Manager).
Copy the code below and save it in your home directory as '[color=SeaGreen].firefox-mailto-fix.sh[/color]'  ```
#!/bin/bash
# This script allows FireFox to send mailto: links
# to Thunderbird

THUNDERBIRD="/usr/bin/mozilla-thunderbird"
THUNDERBIRD_REMOTE="/usr/lib/mozilla-thunderbird/mozilla-thunderbird-xremote-client"

#echo "Firefox mailto: $*" >> $HOME/log.txt

MAILTO_URL="$1"
#Strip off the protocol as this confuses Thunderbird
MAIL_DATA=`echo "$MAILTO_URL" | /bin/sed -s 's/^mailto://'`

if $THUNDERBIRD_REMOTE 'ping()' ; then
	$THUNDERBIRD_REMOTE "mailto( $MAIL_DATA )"
else
	#The mailto needs to be in the format mailto:someone@example.com
	#eg not mailto://someone@example.com
	$THUNDERBIRD -P default -compose "$MAILTO_URL"
fi
exit 0
```
Make the script executable by typing in a term window: [color=SeaGreen]chmod 744 ~/.firefox-mailto-fix.sh[/color]
Open the url "about:config" in Firefox.
If you've tried any of the suggested fixes in these forums, you already have a key named '[color=Red]network.protocol-handler.app.mailto[/color]'. Use the filter box to eliminate the  other keys.
If you don't have the key, right click and add it.
Give it the value [color=SeaGreen]/home/*[user]*/.firefox-mailto-fix.sh[/color] (replace [color=SeaGreen]*[user]*[/color] with your username).
* Voila*. Now Firefox and Thunderbird play nice again and should *continue* to play nice unless Mozilla makes ***drastic*** changes to the API.

---

### Post by quick_snack on 2005-03-14
Thanks, that helped a lot. I am only having the problem now that the focus isn't changed. I have to select the compose-window each time.

Have you an solution for that too?  :grin: 

Karel

---

### Post by lordofkhemenu on 2005-03-14
[QUOTE=quick_snack]Thanks, that helped a lot. I am only having the problem now that the focus isn't changed. I have to select the compose-window each time.

Have you an solution for that too?  :grin: 

Karel[/QUOTE]
It does bring it to the front for me, but didn't used to..must be a setting somewhere..
In 'preferred applications' I have firefox set as the browser (not 'debian sensible browser') and 'thunderbird' as mail reader (not custom|mozilla-thunderbird), but after playing with those settings to see if it made a difference, they're not affecting it..the compose window comes to the front automagically.
All I can suggest is play with focus settings (system|preferences|windows) and others to see what happens.

[edit] It doesn't always work..sometimes the compose windows stays at the back
It's a minor annoyance that I can live with.

---

### Post by bonifacio on 2005-03-18
I did mine differently.

Applications/System Tools/Configuration Editor

Look for...
Key name: /desktop/gnome/url-handlers/mailto/command
Key value: /usr/bin/mozilla-thunderbird %s (originally points to evolution)

Hope it helps.

Ammendment:
Apparently this only works if Thunderbird is not yet running if it was then you'll be bugged with the "Choose User Profile" dialog box.  If that's the case follow the origin of this thread.

---

### Post by easy_target on 2005-06-24
Thank you Bonifacio. Your solution works perfectly for me!

---

### Post by pangloss on 2005-06-28
**edit:** as pointed out in [this thread](http://ubuntuforums.org/showthread.php?t=22333), the problem in Hoary is simply that /usr/bin/mozilla-thunderbird needs to have the string "Mozilla-Thunderbird" replaced with "mozilla-thunderbird" and you will achieve exactly the same behavior as the script below. 
**/edit**

I use the following script, and set it as Gnome's preferred mail reader as well as the exec target for the Thunderbird launcher(s).

```

#!/bin/bash
# This script allows FireFox to send mailto: links
# to Thunderbird
# Helper script for Thunderbird that
#   - starts Thunderbird if it's not already running, raising a window otherwise
#   - opens a compose window if called with a mailto: argument
#
# USAGE:
#   - THUNDERBIRD must point to the thunderbird executable
#   - either:
#       + set network.protocol-handler.app.mailto to point to this script
#       + call this script in place of the thunderbird executable (e.g. in
#         Gnome's Preferred Applications Mail Reader and any Thunderbird
#         launchers)

THUNDERBIRD="/usr/bin/mozilla-thunderbird"

$THUNDERBIRD -remote 'ping()' || exec $THUNDERBIRD "$@" # exec thunderbird if there’s no instance running
$THUNDERBIRD -remote "xfeDoCommand(openInbox)" # otherwise raise window,
[ "${1%%:*}" = 'mailto' ] && $THUNDERBIRD -remote "mailto(${1#mailto:})" # and maybe send the mailto:
```

---

### Post by BigDoug on 2007-11-23
I'm a desktop Ubuntu user, an average Joe, learning Linux, not a guru, not a qualified hacker, so perhaps someone more experienced may be kind enough to correct any errors here. 
 
After installing Swiftweasel the browser would no longer open “mailto:” links by launching Thunderbird. Firefox developed the same problem. 
It may not be from installing Swiftweasel, because various forums report this problem with Firefox and Thunderbird not working together with mailto links in websites after updates. 
 
At some point my /usr/bin/mozilla-thunderbird was changed to /usr/bin/thunderbird (a link to a script in /usr/lib/thunderbird/thunderbird). So first check /usr/bin and if you only have thunderbird and mozilla (which links to the script /usr/local/bin/swiftweasel32 – hence my hunch that this problem developed when installing Swiftweasel)there, and not mozilla-thunderbird, this may help. The more complex solutions suggested in various forums may not be needed and did not work for me. 
 
I run Ubuntu 7.10 Gutsy Gibbon 64-bit with 32-bit Firefox, and now, joyfully, Swiftweasel, its soooo much faster. 
 
Here is the technique I used to make mailto links point from Swiftweasel and Firefox to Thunderbird – it is in part borrowed from fixes reported in various forums.  
 
1) Launch Swiftweasel or Firefox and view the configuration strings using the URL 
about:config 
 
2) using the field at the top, search for 
mailto 
 
3) If you do NOT have network.protocol-handler.app.mailto (normally 
you don't), create it using these steps: 
a) right-click 
b) choose New --> String 
c) new string: network.protocol-handler.app.mailto 
d) new value: /usr/bin/thunderbird 
 
4) If you already see an entry for 
network.protocol-handler.app.mailto, verify the path to the mail 
client. Double click the string to set it if necessary. Also be sure 
network.protocol-handler.external.mailto is set to true 
 
5) Do the same in Firefox. Voila! website links mailto: now launch Thunderbird. 
 
For the sake of curiosity, does anyone know if this was an update problem or a byproduct of the Swiftweasel installation? Or am I way off the mark?.

---

### Post by iansane on 2008-01-18
> **bonifacio said:**
> I did mine differently.

Applications/System Tools/Configuration Editor

Look for...
Key name: /desktop/gnome/url-handlers/mailto/command
Key value: /usr/bin/mozilla-thunderbird %s (originally points to evolution)

Hope it helps.

Ammendment:
Apparently this only works if Thunderbird is not yet running if it was then you'll be bugged with the "Choose User Profile" dialog box.  If that's the case follow the origin of this thread.

I went to system>preferences>prefered applications, and set it there.

I had to edit menus and add the configuration tool to system tools but did it out of curiosity. When I followed the path and found the key listed above it was already set.

I don't have an entry for network.protocol-handler.mailto at all in the "about:config" in firefox and it all still works perfectly. 

It might have something to do with the fact that I have a fresh install of Gutsy and the newest updated stable releases of thunderbird and firefox from the repos, but it is perfect. Thanks for the how-to's

yeah, I know the post is old but it helped me.

---

### Post by pirog on 2009-06-22
i found that the system-wide configuration is set through "System Tools -> Config Editor" (see above). this will allow you to click e-mail addresses anywhere in the system (Tomboy, OO, etc.) and it'll take you to the e-mail editor (Thunderbird in my case)

to fix firefox issue only, choose "Edit -> Prefs -> App tab", search for "mail" and from the drop-down use the default value or "Use other" and then choose location of Thunderbird (/usr/bin/thunderbird in my case)

cheers bonifacio,

Vlad.

---

### Post by McEye on 2011-08-09
> **pirog said:**
> i found that the system-wide configuration is set through "System Tools -> Config Editor" (see above). this will allow you to click e-mail addresses anywhere in the system (Tomboy, OO, etc.) and it'll take you to the e-mail editor (Thunderbird in my case)

to fix firefox issue only, choose "Edit -> Prefs -> App tab", search for "mail" and from the drop-down use the default value or "Use other" and then choose location of Thunderbird (/usr/bin/thunderbird in my case)

cheers bonifacio,

Vlad.

That did it for me. Thanks.

---

