---
title: "Please Test My Commandline Facebook Program (Installer Script)"
date: 2008-12-10
forum: Programming Talk
---

### Post by tdrusk on 2008-12-10
**Code doesn't work atm. Check back later.**
I wrote the installer scripts.

Please run fbcmdInstaller.
```
sudo bash fbcmdInstaller_0.2.sh
```When that's done test it with
```
fbcmd
```Then if you want to remove it run
```
sudo bash fbcmdRemove_0.2.sh
```

---

### Post by mssever on 2008-12-10
> **tdrusk said:**
> I wrote the installer scripts.

Please run fbcmdInstaller.
```
sudo sh fbcmdInstaller.sh
```When that's done test it with
```
fbcmd
```Then if you want to remove it run
```
sudo sh fbcmdRemove.sh
```
I haven't run your scripts, since I don't use Facebook, but I have looked at them and have some comments:
```
[COLOR=#408080][I]#!/bin/bash
#Installs fbcmd to /usr/lib/fbcmd
[/I][/COLOR]
[COLOR=#408080][I]#Get dependencies
[/I][/COLOR]apt-get install php5-cli

[COLOR=#408080][I]#make new directory for installation
[/I][/COLOR]mkdir /usr/lib/fbcmd

[COLOR=#408080][I]#Get fbcmd
[/I][/COLOR]wget --directory-prefix[COLOR=#666666]=[/COLOR]/usr/lib/fbcmd http://www.cs.ubc.ca/~davet/fbcmd/fbcmd-0-90.tgz

[COLOR=#408080][I]#extract
[/I][/COLOR][COLOR=#008000]cd[/COLOR] /usr/lib/fbcmd/
tar -xvf /usr/lib/fbcmd/fbcmd-0-90.tgz 

[COLOR=#408080][I]#Which browser?
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Type the command to start your browser (ex: firefox, konqueror, etc)"[/COLOR]
[COLOR=#008000]read [/COLOR]BROWSER
```Instead of asking which browser the user's running, just use xdg-open, which will start the default browser.
```
[COLOR=#408080][I]#Close Browser
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Close your browser. Press Enter/Return when ready."[/COLOR]
[COLOR=#008000]read [/COLOR]ENTER
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Wait..."[/COLOR]
sleep 5
```Why should the user close their browser before it has even been opened? Also, the sleep 5 only wastes time. If the user closes their browser, then hits enter, the browser is dead. But again, closing the browser is pointless.
```
[COLOR=#408080][I]#Get AUTH code
[/I][/COLOR][COLOR=#19177c]$BROWSER[/COLOR] [COLOR=#ba2121]"http://www.facebook.com/code_gen.php?v=1.0&api_key=d96ea311638cf65f04b33c87eacf371e"[/COLOR] &

[COLOR=#408080][I]#Ask for AUTH code
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"What is your AUTH code?"[/COLOR]
[COLOR=#008000]read [/COLOR]ANSWER

[COLOR=#408080][I]#Enters AUTH code
[/I][/COLOR]php /usr/lib/fbcmd/fbcmd/fbcmd.php AUTH [COLOR=#19177c]$ANSWER[/COLOR]

[COLOR=#408080][I]#Asks for user name
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"What is your user/login name on this Linux computer?"[/COLOR]
[COLOR=#008000]read [/COLOR]NAME
```You can detect this easily enough. Just look at $USER. If the script is running under sudo, then look at $SUDO_USER. The command env shows you all kinds of useful environment variables. And if you run sudo env, you'll see what's available from there.
```
[COLOR=#408080][I]#Create alias
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"alias fbcmd='php /usr/lib/fbcmd/fbcmd/fbcmd.php'"[/COLOR] >> /home/[COLOR=#19177c]$NAME[/COLOR]/.bashrc

[COLOR=#408080][I]#Add to .bash_aliases
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"if [ -f ~/.bash_aliases ]; then 
   . ~/.bash_aliases
fi"[/COLOR] >> /home/[COLOR=#19177c]$NAME[/COLOR]/.bashrc
```I think you meant /home/$USER/*. But even that's incorrect, because you can't determine a user's home directory from their username. For example, in a default installation, root's home dir is /root, not /home/root. Furthermore, there's nothing preventing user bob from having his homedir in /home/jane or /usr/local/foo/bob/home/directory. The env variable $HOME gives the correct home directory. You could also refer to ~$USER/some/file (or ~$SUDO_USER).

Another problem is that you add code to ~/.bashrc to source ~/.bash_aliases, but you never do anything with .bash_aliases. You put your alias directly in .bashrc.

Finally, if I ran an installer and found that it had modified my .bashrc behind my back, I'd be upset. Installers have no business doing that. Instead, it should add a symlink to the script somewhere on the PATH. The recommended way of doing this is ```
ln -s /usr/lib/fbcmd/fbcmd/fbcmd.php /usr/local/bin/fbcmd
``````
[COLOR=#408080][I]#Allow all users to use
[/I][/COLOR]chmod 666 /home/[COLOR=#19177c]$NAME[/COLOR]/.bashrc
```Why would you allow all users to use a user's .bashrc? That defeats the point of having per-user settings. If you really want global settings, set them in /etc/profile. Any time you're using a dotfile in the users homedir that won't work with 600 (or 700) permissions, you're using it wrong.
```
[COLOR=#408080][I]#Clean up
[/I][/COLOR]rm /usr/lib/fbcmd/fbcmd-0-90.tgz

[COLOR=#408080][I]#Finished
[/I][/COLOR][COLOR=#008000]exit[/COLOR] [COLOR=#408080][I]#
[/I][/COLOR]
```The exit statement really isn't necessary, since the script will automatically exit when it's finished.


The uninstaller:
```
[COLOR=#408080][I]#!/bin/bash
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"What is your linux username?"[/COLOR]
[COLOR=#008000]read [/COLOR]ANSWER
```Again, this is a unnecessary question.
```
rm -r /usr/lib/fbcmd
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Remove the fbcmd and the if command above it from your .bashrc(Wait...)"[/COLOR]
```Yet another reason not to modify the user's .bashrc.
```
sleep 4
nano /home/[COLOR=#19177c]$ANSWER[/COLOR]/.bashrc
[COLOR=#008000]exit[/COLOR] [COLOR=#408080][I]#
[/I][/COLOR]
```The rest of this script is unnecessary. The sleep statement does nothing, and there's no need for nano, because you shouldn't have modified .bashrc in the first place.

EDIT: One more thing. In your instructions, you say to use sh to run your scripts, yet the shebang on both files calls bash. Which is it? Bash and sh are NOT the same thing.

---

### Post by tdrusk on 2008-12-10
double post...

---

### Post by tdrusk on 2008-12-10
> **mssever said:**
> I haven't run your scripts, since I don't use Facebook, but I have looked at them and have some comments:
```
[COLOR=#408080][I]#!/bin/bash
#Installs fbcmd to /usr/lib/fbcmd
[/I][/COLOR]
[COLOR=#408080][I]#Get dependencies
[/I][/COLOR]apt-get install php5-cli

[COLOR=#408080][I]#make new directory for installation
[/I][/COLOR]mkdir /usr/lib/fbcmd

[COLOR=#408080][I]#Get fbcmd
[/I][/COLOR]wget --directory-prefix[COLOR=#666666]=[/COLOR]/usr/lib/fbcmd http://www.cs.ubc.ca/~davet/fbcmd/fbcmd-0-90.tgz

[COLOR=#408080][I]#extract
[/I][/COLOR][COLOR=#008000]cd[/COLOR] /usr/lib/fbcmd/
tar -xvf /usr/lib/fbcmd/fbcmd-0-90.tgz 

[COLOR=#408080][I]#Which browser?
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Type the command to start your browser (ex: firefox, konqueror, etc)"[/COLOR]
[COLOR=#008000]read [/COLOR]BROWSER
```Instead of asking which browser the user's running, just use xdg-open, which will start the default browser.
Thanks, sounds good. 
> 
```
[COLOR=#408080][I]#Close Browser
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Close your browser. Press Enter/Return when ready."[/COLOR]
[COLOR=#008000]read [/COLOR]ENTER
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Wait..."[/COLOR]
sleep 5
```Why should the user close their browser before it has even been opened? Also, the sleep 5 only wastes time. If the user closes their browser, then hits enter, the browser is dead. But again, closing the browser is pointless.
The browser needs to be closed because I couldn't figure out how to make the script open a new tab or open the browser. If you have some insight in this please inform me. 

The sleep is necessary (at least it was for the current script). When I close firefox and just run ```
firefox www.google.com
``` I get an error that Firefox is still running. I have to wait a few seconds. If the browser doesn't open it ruins the script because you need the AUTH.
> 
```
[COLOR=#408080][I]#Get AUTH code
[/I][/COLOR][COLOR=#19177c]$BROWSER[/COLOR] [COLOR=#ba2121]"http://www.facebook.com/code_gen.php?v=1.0&api_key=d96ea311638cf65f04b33c87eacf371e"[/COLOR] &

[COLOR=#408080][I]#Ask for AUTH code
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"What is your AUTH code?"[/COLOR]
[COLOR=#008000]read [/COLOR]ANSWER

[COLOR=#408080][I]#Enters AUTH code
[/I][/COLOR]php /usr/lib/fbcmd/fbcmd/fbcmd.php AUTH [COLOR=#19177c]$ANSWER[/COLOR]

[COLOR=#408080][I]#Asks for user name
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"What is your user/login name on this Linux computer?"[/COLOR]
[COLOR=#008000]read [/COLOR]NAME
```You can detect this easily enough. Just look at $USER. If the script is running under sudo, then look at $SUDO_USER. The command env shows you all kinds of useful environment variables. And if you run sudo env, you'll see what's available from there.
Thanks for this.
> 
```
[COLOR=#408080][I]#Create alias
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"alias fbcmd='php /usr/lib/fbcmd/fbcmd/fbcmd.php'"[/COLOR] >> /home/[COLOR=#19177c]$NAME[/COLOR]/.bashrc

[COLOR=#408080][I]#Add to .bash_aliases
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"if [ -f ~/.bash_aliases ]; then 
   . ~/.bash_aliases
fi"[/COLOR] >> /home/[COLOR=#19177c]$NAME[/COLOR]/.bashrc
```I think you meant /home/$USER/*. But even that's incorrect, because you can't determine a user's home directory from their username. For example, in a default installation, root's home dir is /root, not /home/root. Furthermore, there's nothing preventing user bob from having his homedir in /home/jane or /usr/local/foo/bob/home/directory. The env variable $HOME gives the correct home directory. You could also refer to ~$USER/some/file (or ~$SUDO_USER).

Another problem is that you add code to ~/.bashrc to source ~/.bash_aliases, but you never do anything with .bash_aliases. You put your alias directly in .bashrc.

Finally, if I ran an installer and found that it had modified my .bashrc behind my back, I'd be upset. Installers have no business doing that. Instead, it should add a symlink to the script somewhere on the PATH. The recommended way of doing this is ```
ln -s /usr/lib/fbcmd/fbcmd/fbcmd.php /usr/local/bin/fbcmd
``````

Thanks. Will fix.
> 
[COLOR=#408080][I]#Allow all users to use
[/I][/COLOR][code]chmod 666 /home/[COLOR=#19177c]$NAME[/COLOR]/.bashrc
```Why would you allow all users to use a user's .bashrc? That defeats the point of having per-user settings. If you really want global settings, set them in /etc/profile. Any time you're using a dotfile in the users homedir that won't work with 600 (or 700) permissions, you're using it wrong.
How can I make it so the user can access the file like before.
> 
```
[COLOR=#408080][I]#Clean up
[/I][/COLOR]rm /usr/lib/fbcmd/fbcmd-0-90.tgz

[COLOR=#408080][I]#Finished
[/I][/COLOR][COLOR=#008000]exit[/COLOR] [COLOR=#408080][I]#
[/I][/COLOR]
```The exit statement really isn't necessary, since the script will automatically exit when it's finished.
ah cool

> 
The uninstaller:
```
[COLOR=#408080][I]#!/bin/bash
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"What is your linux username?"[/COLOR]
[COLOR=#008000]read [/COLOR]ANSWER
```Again, this is a unnecessary question. thanks
> 
```
rm -r /usr/lib/fbcmd
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Remove the fbcmd and the if command above it from your .bashrc(Wait...)"[/COLOR]
```Yet another reason not to modify the user's .bashrc.
```
sleep 4
nano /home/[COLOR=#19177c]$ANSWER[/COLOR]/.bashrc
[COLOR=#008000]exit[/COLOR] [COLOR=#408080][I]#
[/I][/COLOR]
```The rest of this script is unnecessary. The sleep statement does nothing, and there's no need for nano, because you shouldn't have modified .bashrc in the first place.

Aight cool. I left the sleep statement so the user would have time to read it, but I won't need that anymore.
> 
EDIT: One more thing. In your instructions, you say to use sh to run your scripts, yet the shebang on both files calls bash. Which is it? Bash and sh are NOT the same thing.
I just realized that too. Would I omit that first line if I wanted to run them with sh?

Thanks so much for your help. I have never written a script like this and I need all the crit I can get.

---

### Post by mssever on 2008-12-10
> **tdrusk said:**
> The browser needs to be closed because I couldn't figure out how to make the script open a new tab or open the browser. If you have some insight in this please inform me.When I type either "xdg-open http://www.google.com" or "firefox http://www.google.com" I get a new tab in the currently-running firefox instance. My [gmail_link]("http://ubuntuforums.org/showthread.php?t=398974") script includes the following function to launch a URL in a browser. I wrote this before I knew about xdg-open, so it includes a bit of logic to work out which browser to open. I include this because Opera is a different beast from the rest--unless they've fixed it by now. Anyway, here's a code snippet: ```
function callBrowser {
    local ua="$1"  # User-agent, aka browser
    local url="$2"

    if [[ $ua == 'opera' ]]; then
        exec opera --remote "openURL($url,new-page)"
    else exec $ua "$url"
    fi
}
```Of course, in your case you'd need to drop the exec.

> How can I make it so the user can access the file like before.Don't change .bashrc in the first place. Then there will be no work to do.

Oh, if your script happens to create any files, remember that those files will be owned by root, since the script is running as root. So you might need to chown stuff (anything you install in the user's home directory chould be chowned to the user).
> I just realized that too. Would I omit that first line if I wanted to run them with sh?It's always a good idea to include a shebang, because many people will set the x-bit on your file and run it with ./fbcmdInstaller.sh. If you want it to run with sh, set the shebang to #!/bin/sh. But IMO there are very few reasons to prefer sh over bash these days. And bash is a known quantity. sh will vary a bit. For example, on many Linux systems, sh actually runs bash in reduced-feature mode. In Ubuntu, sh runs dash. Other systems might use something else for sh. And every shell will have its own corner cases. With bash, you know what you're getting, and the odds of running into a system without bash are slim (and the odds of a Linux system without bash are virtually nil).

So my recommendation is to leave the shebang as is, and amend your instructions to either tell the user to make the file executable and then directly execute it, or to call it with "bash filename".

EDIT: One more thing: If you explicitly name an interpreter (sh somefile, bash somefile, php somefile), then it doesn't matter whether the file is executable.

---

### Post by tdrusk on 2008-12-10
> **mssever said:**
> When I type either "xdg-open http://www.google.com" or "firefox http://www.google.com" I get a new tab in the currently-running firefox instance. My [gmail_link]("http://ubuntuforums.org/showthread.php?t=398974") script includes the following function to launch a URL in a browser. I wrote this before I knew about xdg-open, so it includes a bit of logic to work out which browser to open. I include this because Opera is a different beast from the rest--unless they've fixed it by now. Anyway, here's a code snippet: ```
function callBrowser {
    local ua="$1"  # User-agent, aka browser
    local url="$2"

    if [[ $ua == 'opera' ]]; then
        exec opera --remote "openURL($url,new-page)"
    else exec $ua "$url"
    fi
}
```Of course, in your case you'd need to drop the exec.

Don't change .bashrc in the first place. Then there will be no work to do.

Oh, if your script happens to create any files, remember that those files will be owned by root, since the script is running as root. So you might need to chown stuff (anything you install in the user's home directory chould be chowned to the user).
It's always a good idea to include a shebang, because many people will set the x-bit on your file and run it with ./fbcmdInstaller.sh. If you want it to run with sh, set the shebang to #!/bin/sh. But IMO there are very few reasons to prefer sh over bash these days. And bash is a known quantity. sh will vary a bit. For example, on many Linux systems, sh actually runs bash in reduced-feature mode. In Ubuntu, sh runs dash. Other systems might use something else for sh. And every shell will have its own corner cases. With bash, you know what you're getting, and the odds of running into a system without bash are slim (and the odds of a Linux system without bash are virtually nil).

So my recommendation is to leave the shebang as is, and amend your instructions to either tell the user to make the file executable and then directly execute it, or to call it with "bash filename".

EDIT: One more thing: If you explicitly name an interpreter (sh somefile, bash somefile, php somefile), then it doesn't matter whether the file is executable.> **mssever said:**
> I haven't run your scripts, since I don't use Facebook, but I have looked at them and have some comments:
```
[COLOR=#408080][I]#!/bin/bash
#Installs fbcmd to /usr/lib/fbcmd
[/I][/COLOR]
[COLOR=#408080][I]#Get dependencies
[/I][/COLOR]apt-get install php5-cli

[COLOR=#408080][I]#make new directory for installation
[/I][/COLOR]mkdir /usr/lib/fbcmd

[COLOR=#408080][I]#Get fbcmd
[/I][/COLOR]wget --directory-prefix[COLOR=#666666]=[/COLOR]/usr/lib/fbcmd http://www.cs.ubc.ca/~davet/fbcmd/fbcmd-0-90.tgz

[COLOR=#408080][I]#extract
[/I][/COLOR][COLOR=#008000]cd[/COLOR] /usr/lib/fbcmd/
tar -xvf /usr/lib/fbcmd/fbcmd-0-90.tgz 

[COLOR=#408080][I]#Which browser?
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Type the command to start your browser (ex: firefox, konqueror, etc)"[/COLOR]
[COLOR=#008000]read [/COLOR]BROWSER
```Instead of asking which browser the user's running, just use xdg-open, which will start the default browser.
Thanks, sounds good. 
> 
```
[COLOR=#408080][I]#Close Browser
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Close your browser. Press Enter/Return when ready."[/COLOR]
[COLOR=#008000]read [/COLOR]ENTER
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Wait..."[/COLOR]
sleep 5
```Why should the user close their browser before it has even been opened? Also, the sleep 5 only wastes time. If the user closes their browser, then hits enter, the browser is dead. But again, closing the browser is pointless.The browser needs to be closed because I couldn't figure out how to make the script open a new tab or open the browser. If you have some insight in this please inform me. 

The sleep is necessary (at least it was for the current script). When I close firefox and just run ```
firefox www.google.com
``` I get an error that Firefox is still running. I have to wait a few seconds. If the browser doesn't open it ruins the script because you need the AUTH.
> 
```
[COLOR=#408080][I]#Get AUTH code
[/I][/COLOR][COLOR=#19177c]$BROWSER[/COLOR] [COLOR=#ba2121]"http://www.facebook.com/code_gen.php?v=1.0&api_key=d96ea311638cf65f04b33c87eacf371e"[/COLOR] &

[COLOR=#408080][I]#Ask for AUTH code
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"What is your AUTH code?"[/COLOR]
[COLOR=#008000]read [/COLOR]ANSWER

[COLOR=#408080][I]#Enters AUTH code
[/I][/COLOR]php /usr/lib/fbcmd/fbcmd/fbcmd.php AUTH [COLOR=#19177c]$ANSWER[/COLOR]

[COLOR=#408080][I]#Asks for user name
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]""[/COLOR]
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"What is your user/login name on this Linux computer?"[/COLOR]
[COLOR=#008000]read [/COLOR]NAME
```You can detect this easily enough. Just look at $USER. If the script is running under sudo, then look at $SUDO_USER. The command env shows you all kinds of useful environment variables. And if you run sudo env, you'll see what's available from there.Thanks for this.
> 
```
[COLOR=#408080][I]#Create alias
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"alias fbcmd='php /usr/lib/fbcmd/fbcmd/fbcmd.php'"[/COLOR] >> /home/[COLOR=#19177c]$NAME[/COLOR]/.bashrc

[COLOR=#408080][I]#Add to .bash_aliases
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"if [ -f ~/.bash_aliases ]; then 
   . ~/.bash_aliases
fi"[/COLOR] >> /home/[COLOR=#19177c]$NAME[/COLOR]/.bashrc
```I think you meant /home/$USER/*. But even that's incorrect, because you can't determine a user's home directory from their username. For example, in a default installation, root's home dir is /root, not /home/root. Furthermore, there's nothing preventing user bob from having his homedir in /home/jane or /usr/local/foo/bob/home/directory. The env variable $HOME gives the correct home directory. You could also refer to ~$USER/some/file (or ~$SUDO_USER).

Another problem is that you add code to ~/.bashrc to source ~/.bash_aliases, but you never do anything with .bash_aliases. You put your alias directly in .bashrc.

Finally, if I ran an installer and found that it had modified my .bashrc behind my back, I'd be upset. Installers have no business doing that. Instead, it should add a symlink to the script somewhere on the PATH. The recommended way of doing this is ```
ln -s /usr/lib/fbcmd/fbcmd/fbcmd.php /usr/local/bin/fbcmd
```Thanks. Will fix.
> 
[COLOR=#408080][I]#Allow all users to use
[/I][/COLOR]chmod 666 /home/[COLOR=#19177c]$NAME[/COLOR]/.bashrc[/code]> Why would you allow all users to use a user's .bashrc? That defeats the point of having per-user settings. If you really want global settings, set them in /etc/profile. Any time you're using a dotfile in the users homedir that won't work with 600 (or 700) permissions, you're using it wrong.How can I make it so the user can access the file like before.
> 
```
[COLOR=#408080][I]#Clean up
[/I][/COLOR]rm /usr/lib/fbcmd/fbcmd-0-90.tgz

[COLOR=#408080][I]#Finished
[/I][/COLOR][COLOR=#008000]exit[/COLOR] [COLOR=#408080][I]#
[/I][/COLOR]
```The exit statement really isn't necessary, since the script will automatically exit when it's finished.ah cool

> 
The uninstaller:
```
[COLOR=#408080][I]#!/bin/bash
[/I][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"What is your linux username?"[/COLOR]
[COLOR=#008000]read [/COLOR]ANSWER
```Again, this is a unnecessary question. thanks
> 
```
rm -r /usr/lib/fbcmd
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"Remove the fbcmd and the if command above it from your .bashrc(Wait...)"[/COLOR]
```Yet another reason not to modify the user's .bashrc.
```
sleep 4
nano /home/[COLOR=#19177c]$ANSWER[/COLOR]/.bashrc
[COLOR=#008000]exit[/COLOR] [COLOR=#408080][I]#
[/I][/COLOR]
```The rest of this script is unnecessary. The sleep statement does nothing, and there's no need for nano, because you shouldn't have modified .bashrc in the first place.
Aight cool. I left the sleep statement so the user would have time to read it, but I won't need that anymore.
> 
EDIT: One more thing. In your instructions, you say to use sh to run your scripts, yet the shebang on both files calls bash. Which is it? Bash and sh are NOT the same thing.I just realized that too. Would I omit that first line if I wanted to run them with sh?

Thanks so much for your help. I have never written a script like this and I need all the crit I can get.
Thanks. Very useful info. I'm going to work on this more tomorrow. Brain is tired.

---

### Post by tdrusk on 2008-12-11
Aight. I have the program running good. I was just wondering what I should do with the /usr/local/bin/fbcmd? How can I make it so a normal user can use it?

---

### Post by mssever on 2008-12-11
> **tdrusk said:**
> Aight. I have the program running good. I was just wondering what I should do with the /usr/local/bin/fbcmd? How can I make it so a normal user can use it?
If it's a symlink, everyone can use it, provided the target has the proper permissions (execute and all that). Also, since the target is apparently a command-line PHP script, make sure the script has an appropriate shebang line.

Alternatively, fbcmd could easily be a shell script wrapper that merely calls the target with any necessary command-line arguments, environment, etc. Of course, the wrapper still must be executable and have an appropriate shebang. In either case, I recommend the permissions 755.

---

### Post by tdrusk on 2008-12-11
Okay. The new and improved scripts are up. What should I name them? (.py,.sh) 
I know it doesn't matter since I'm calling bash, but still...

---

### Post by mssever on 2008-12-11
> **tdrusk said:**
> Okay. The new and improved scripts are up. What should I name them? (.py,.sh) 
I know it doesn't matter since I'm calling bash, but still...
Don't use .py unless they're written in Python. .sh is a good choice, as is the nonstandard-but-clear .bash. Of course, since executables traditionally have no extension, you could simply omit the extension altogether. Remember, the main purpose of extensions in the *nix world is to give human users some idea of the file's type. The system doesn't care. If the user sees .sh, they'll assume a shell script of some sort. If they see .py, they'll assume it's written in Python. Whatever you do is fine, as long as you don't mislead people.

One other convention to be aware of is that uppercase letters are generally not used in filenames (with a few prominant exceptions, such as X). Generally, words are separated with either hyphens or underscores (or abbreviated, though I personally tend to avoid all but the best-established abbreviations because other people might not understand some abbreviation I just invented.

---

### Post by G|N| on 2008-12-11
Hello,

I made a script that shows the facebook messages, notifications, friend requests and wall posts.

It is far from perfect but maybe somebody can use it as an example :)

It is written in python.

If you want to test it:
1) Put your username and password in the variables
```

user = ""
passwd = ""

```

2) run the script
```
python facebook.py
```

---

### Post by tdrusk on 2008-12-11
> **G|N| said:**
> Hello,

I made a script that shows the facebook messages, notifications, friend requests and wall posts.

It is far from perfect but maybe somebody can use it as an example :)

It is written in python.

If you want to test it:
1) Put your username and password in the variables
```

user = ""
passwd = ""net yesterday if you didn't know already [http://tinyurl.com/5rvzyt](http://tinyurl.com/5rvzyt)

```2) run the script
```
python facebook.py
```
 
I put in my username and password but I didn't get any output.

---

### Post by mssever on 2008-12-11
> **G|N| said:**
> I made a script that shows the facebook messages, notifications, friend requests and wall posts.
Are you aware of Beautiful Soup? It's an HTML parser for Python, which beats trying to use regexps to parse HTML.

---

### Post by G|N| on 2009-01-06
It seems like facebook changed their html so here is an updated version from my facebook python class:

You can use it like this:
```

import facebook
f = facebook.Facebook("myemail@email.com", "secretpass")

```

Messages:
```

messages = f.get_messages()

for m in messages:
  print m.sender + ": " + m.message

```

Notifications:
```

notifications = f.get_notifications()

for n in notifications :
  print n.notification

```

Requests:
```

requests= f.get_requests()

for r in requests:
  print r.request

```

Wall:
```

wall= f.get_wall()

for w in wall:
  print w.poster + ": " + w.post

```

Enjoy!

---

### Post by drubin on 2009-01-06
Not sure if this is relavant but when I was doing facebook appliation development for web. we used to keep the $Secretkey private because having access to it means being able to publish stuff as your application..
```
$fbCmdAppSecret = '************';
```

Not so sure how relevant that is for CLI applications

---

### Post by G|N| on 2009-01-06
> **drubin said:**
> Not sure if this is relavant but when I was doing facebook appliation development for web. we used to keep the $Secretkey private because having access to it means being able to publish stuff as your application..
```
$fbCmdAppSecret = '************';
```

Not so sure how relevant that is for CLI applications

For my code it is not relevant because it isn't a facebook application...it is an application that reads facebook messages, wall posts,... by logging in and scraping the content

---

### Post by drubin on 2009-01-06
> **G|N| said:**
> For my code it is not relevant because it isn't a facebook application...it is an application that reads facebook messages, wall posts,... by logging in and scraping the content

I wasn't refering to your application. You do not use the facebook client libs. And do not have the $secrete any thing in your applications.

ps python doesn't use $var to signify variables. :)

---

