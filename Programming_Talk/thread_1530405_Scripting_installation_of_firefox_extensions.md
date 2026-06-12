---
title: "Scripting installation of firefox extensions"
date: 2010-07-13
forum: Programming Talk
---

### Post by shaggy999 on 2010-07-13
I'm trying to figure out how to install firefox xpi extensions from a scripted environment and running into trouble. My understanding is that you can do this by running the following command:

```
firefox -install-global-extension "<path-to-extension>\extname.xpi"

```

Unfortunately, all this does is start firefox. Anybody have any idea why this doesn't work? Here's my current script:

```

TMPDIR=`mktemp -d`
cd $TMPDIR

# Grab flashblock
wget https://addons.mozilla.org/en-US/firefox/downloads/latest/433/addon-433-latest.xpi?src=addondetail

# Grab adblock plus
wget https://addons.mozilla.org/en-US/firefox/downloads/latest/1865/addon-1865-latest.xpi?src=addondetail

for FILE in $TMPDIR/*.xpi ; do
	firefox -install-global-extension "$FILE"
done

```

I've tried executing these commands manually just to confirm, but it just doesn't work.

---

### Post by kitrule on 2011-01-18
Try it with sudo. e.g. sudo <your script>
or sudo firefox -install-global-extension "<path-to-extension>\extname.xpi"

Alternatively, look here for a method avoiding -install-global-extension altogether.
-> [http://ubuntuforums.org/showpost.php?p=10372816&postcount=11](http://ubuntuforums.org/showpost.php?p=10372816&postcount=11)

---

