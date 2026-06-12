---
title: "HOWTO: Feed the Cookie Monster"
date: 2009-01-30
forum: Outdated Tutorials &amp; Tips
---

### Post by glotz on 2009-01-30
This howto is about setting up a smart button to display you "random, hopefully interesting, adages". See the fortunez.jpg attachment how it all looks in action, the little wise a$$ text on the screen is our objective and the first button on the lower panel is how it's operated. Clicking on the button shows a random proverb for you and clicking it again hides it.

For the more technical readers, we're going to setup conky to display fortunes. (This howto needs some editing if you're already using conky. Just make the script operate on the last instance of conky.)

First, we fetch the needed packages, use your favourite package management solution, e.g.
```
sudo apt-get install fortunes conky
```

Then we make the actual button. Right click on the panel > add to panel > custom app launcher > add > name: Fortunes > command: /home/**<yourusername>**/fortunes > click on the icon and point it to my cool fortune cookie image (included in the post attachments) > ok

(naturally **<yourusername>** is to be replaced with ...your username)

And then we edit the script to launch conky. Drop to terminal and type in
```
nano /home/**<yourusername>**/fortunes
``` Then copy paste there the following
```
if !(ps -C conky |grep conky > /dev/null)
then
conky --config=/home/**<yourusername>**/.conkyrcFORTUNE
else pkill conky
fi

```
Be sure to change that username there. Then hit Ctrl+X and save the file with the proposed name (Enter). The script's "smart" logic will kill conky if it's active (i.e. you're already displaying a fortune) and invoke it otherwise. We need to make the script executable, that's done by
```
chmod +x /home/**<yourusername>**/fortunes
```

Finally we edit the conky configuration file for this purpose. In the terminal
```
nano /home/**<yourusername>**/.conkyrcFORTUNE
``` And the following text goes therein
```
update_interval 600
use_xft yes
xftfont terminus:size=17
alignment tl
draw_shades yes
gap_x 35
gap_y 45
maximum_width 1100
TEXT
${color white}
${exec fortune -s -n 320}

```Again, close nano with Ctrl+X and Enter to save to the suggested filename.

That's it, start clicking away!

There are available quite a selection of different fortunes, e.g. localized or offensive, etc in different packages. You might want to change the location to lower left corner or the color of the text. Have fun!

---

