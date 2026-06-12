---
title: "Issues with Google Chrome. Chrome dies upon launch."
date: 2016-04-02
forum: New to Ubuntu
---

### Post by ahears on 2016-04-02
I am running Ubuntu 14.04 64 bit and was using Google Chrome fully updated until last night. I guess when you have Chrome open for long periods of time it will update in the background and then tell you your current version is out of date  and that it "needs an update" until you restart Chrome. Chrome wanted an update, so I restarted the browser to make it go away as usual. Then it gave me the update message again. Anyway I wasn't able to get this notice to go away so I un-installed it and have re-downloaded it, the signing key, and enabled the repository for 64 bit but to no avail. It will install/un-install no problem but when launching I get the following error on the command line:

$ google-chrome-stable

Screen output:

```


LaunchProcess: failed to execvp:
/opt/google/chrome/chrome

```

Then I type '$ps ax | grep -i chrome' which produces the existence of a Sleeping Process and the Zombie...

```


8667 ?        Sl     0:00 /opt/google/chrome/chrome    
 8680 ?        Z      0:00 [chrome] <defunct>


```

 I removed everything with a 'apt-get purge google-chrome-stable' and started over. I have also used 'apt-get clean', 'apt-get autoclean', 'apt-get remove', and 'apt-get autoremove' to clean up the system cache. I installed the Signing Key with 'wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -' which gave me the -OK as expected.

```


OK


```

I checked the Signing Key: 'sudo apt-key list | grep -A1 -B1 -i google'

```


pub   1024D/7FAC5991 2007-03-08
uid                  Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
sub   2048g/C07CB649 2007-03-08


```

I have added the new 64 bit repository *_because the old 32 bitrepositories are offline as of the end of March 2016_*: 'sudo sh -c 'echo "deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google.list'' and finally updated the sources list and installed the browser with: 'sudo apt-get update && sudo apt-get install google-chrome-stable' with no errors.

[B]It blinks on my launcher, then does nothing...
[/B]

I have removed the '~/.config/google-chrome' folder and removed the '/opt/google/chrome' folder after a clean un-install. I have used 'apt-get install -f' to fix broken packages. I have rebuilt the packages list by using 'sudo rm /etc/apt/sources.list' then 'sudo software-properties-gtk' to force a rebuild. I used 'sudo apt-get remove --purge google-chrome-stable' to remove Chrome. I used 'sudo apt-get update && sudo apt-get dist-upgrade -y' to make everything current...At some point I even removed the install/uninstall scripts with 'sudo rm /var/lib/dpkg/info/google-chrome-stable*.prerm' and 'sudo rm /var/lib/dpkg/info/google-chrome-stable*.postinst'. I can't get a fresh install of Google Chrome 64 bit to run. Are the i386 Repositories causing this problem? The 32 bit version worked fine...

[B]

OMG Any help would be a relief please.      Thank you![/B]

---

### Post by QIII on 2016-04-02
Please use default font, size and color.

---

### Post by ahears on 2016-04-02
You specifically have the controls for making these modifications to text, and a help section on how to modify posts using color and tags. The use of color helps to distinguish commands from standard dialogue. Is there an official reason for changing my original post?

---

### Post by QIII on 2016-04-02
The [Ubuntu Forums Rules]("http://ubuntuforums.org/misc.php?do=showrules") link to the [Ubuntu Forums Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"). 

There, you will find the following -- the highlights are mine:



Use color and font properties for highlighting portions of your text, and not for all of the text in your post. ***Please use the default font color and properties*** ***[COLOR="#FF0000"]unless you need to highlight or draw attention to a part of your post[/COLOR]***. ALL CAPS is interpreted as screaming. Funky non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.


As your sections of code are already set off by code tags, no further non-default text properties are necessary.

I would also like to point out the following from the Ubuntu Forums Rules, to which you agreed by creating your account here: 

> Finally, you agree that forum staff have the right to remove, edit, move or close any post, topic or thread at any time they see fit following the guidelines outlined below, or the posting tips which you can find here. 

---

