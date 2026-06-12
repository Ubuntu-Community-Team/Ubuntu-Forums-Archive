---
title: "Tweeting through terminal"
date: 2010-01-16
forum: Outdated Tutorials &amp; Tips
---

### Post by gauthamnagpur18 on 2010-01-16
This is a short tutorial explaining how to post to Twitter using command-line in Linux, without needing to even open up your web browser.

First, install the curl package:

[COLOR="Red"]sudo apt-get install curl[/COLOR]

Next, create a script anywhere in your $PATH, for example twitter.sh inside ~/bin, where ~ is your home directory (make sure ~/bin is included in your $PATHvariable, in case echo $PATH doesn't return it, edit~/.bashrc and add a line like this: export PATH=/home/USER/bin/:$PATH).

The script twitter.sh should contain the following:

#!/bin/bash
curl -u USER:PASS -d status="$*" [http://twitter.com/statuses/update.xml](http://twitter.com/statuses/update.xml) > /dev/null
echo "Message sent!"

Replace USER and PASS with your Twitter username and password, and then make the script executable:

[COLOR="Red"]chmod 755 ~/bin/twitter.sh[/COLOR]

And now test it:

[COLOR="Red"]twitter.sh Hello, world! This is a test.[/COLOR]

So just use it as:

[COLOR="Red"]twitter.sh YOUR MESSAGE[/COLOR]

thanks to [linuxtree]("http://linuxtree.blogspot.com")

---

### Post by Chiapo on 2010-01-17
May I suggest that code which is to be typed into terminal or used in a script be placed within CODE brackets, thus avoiding the "smiley" inclusion?

As your post reads now, one must decipher the ascii text for the particular smiley which appears within the tutorial in order to actually get what you're trying to relate.

Great concept!.

---

### Post by vehka on 2010-01-18
Cool. Now, how to modify the script so that the tweet shows it originated from "command line"? =)

---

### Post by derrick81787 on 2010-01-25
That's cool. Unfortunately, your USER: and then PASS was interpreted as USER: smiley and then censored.  Haha!

---

### Post by mantorpcity on 2010-03-05
Works, thanks for the info.

---

### Post by mistrynitesh on 2010-09-22
any way to do this after the change in authorisation mechanism at twitter?

---

### Post by hocka on 2011-04-12
this doesnt work anymore after OAUTH system... do u have another solution?

---

### Post by mistrynitesh on 2011-04-12
currently I am using 'twidge' which is available in the karmic, maverick and natty repos.

---

### Post by hocka on 2011-04-12
i want to learn the way of sending tweet by using bash script? can anyone help about this?

---

