---
title: "Bash script doesn't run properly from cron"
date: 2010-02-26
forum: Programming Talk
---

### Post by shaggy999 on 2010-02-26
I have a really weird bash script problem that I can not figure out. I actually have two scripts where one calls the other. Here is the first script, which I named "mirror_distro.sh"

mirror_distro.sh
```

#!/bin/bash

HOST="ubuntu.osuosl.org"
ROOT="ubuntu"
METHOD="http"
SECTION="main,restricted,universe,multiverse"
ARCH="i386,amd64"
GENERIC_OPTS="--progress --verbose --nosource --passive --ignore-release-gpg"


# Make sure the directory exists
prep_dir() {
    if [ ! -d "$1" ]; then
        mkdir -p "$1"
    fi
}


# Figure out Distribution to download
DIST=`basename $0|cut -f2 -d "_"`
if [ "$DIST" = "distro.sh" ]; then
	echo "Error!"
	exit 1
fi
LOG="/var/log/$DIST-mirror.log"


# Get Mirror Directory
ABSPATH="$(cd "${0%/*}" 2>/dev/null; echo "$PWD"/"${0##*/}")"
PATH_ONLY=`dirname "$ABSPATH"`
MIRROR_DIR="$PATH_ONLY/$DIST"


# If distribution has been released, include security and update sections
case "$DIST" in 
        "intrepid"|"jaunty"|"karmic" )
                DIST_ALL="$DIST,$DIST-security,$DIST-updates"
                ;;
        * )
                DIST_ALL="$DIST"
                ;;
esac

# Primary Canonical Repositories
prep_dir $MIRROR_DIR/canonical
debmirror $GENERIC_OPTS \
	  --method=rsync \
	  --host=$HOST \
	  --root=:ubuntu \
	  --dist=$DIST_ALL \
	  --section=$SECTION \
	  --arch=$ARCH \
          --getcontents \
	  $MIRROR_DIR/canonical | tee $LOG

# Set up repo to be trusted
wget -N -P $MIRROR_DIR/canonical/dists/$DIST http://$HOST/$ROOT/dists/$DIST/Release.gpg
wget -N -P $MIRROR_DIR/canonical/dists/$DIST-updates http://$HOST/$ROOT/dists/$DIST-updates/Release.gpg
wget -N -P $MIRROR_DIR/canonical/dists/$DIST-security http://$HOST/$ROOT/dists/$DIST-security/Release.gpg

case "$DIST" in
        "intrepid"|"jaunty"|"karmic" )

                # Medibuntu Repository
		prep_dir $MIRROR_DIR/medibuntu
		debmirror $GENERIC_OPTS \
		    --method=http \
		    --host=packages.medibuntu.org \
		    --root=/ \
		    --dist=$DIST \
		    --section="free,non-free" \
		    --arch=$ARCH \
		    $MIRROR_DIR/medibuntu | tee -a $LOG

		wget -N -P $MIRROR_DIR/medibuntu/dists/$DIST http://packages.medibuntu.org/dists/$DIST/Release.gpg

                # Virtualbox
		prep_dir $MIRROR_DIR/virtualbox
		debmirror $GENERIC_OPTS \
		    --method=http \
		    --host=download.virtualbox.org \
		    --root=virtualbox/debian \
		    --dist=$DIST \
		    --section="non-free" \
		    --arch=$ARCH \
		    $MIRROR_DIR/virtualbox | tee -a $LOG

		wget -N -P $MIRROR_DIR/virtualbox/dists/$DIST \
		    http://download.virtualbox.org/virtualbox/debian/dists/$DIST/Release.gpg

		;;

	"lucid" )

		;;
esac

```

This script should be fairly self-explanitory. It's really just a complex wrapper script for the debmirror command. For each distribution (intrepid, jaunty, karmic, lucid) I have a symlink to the mirror_distro.sh file called "mirror_$dist". The filename is used to figure out which distribution to mirror. This script works great normally.

Here's a second script I have called "update.sh":
```

#!/bin/bash
AP="$(cd "${0%/*}" 2>/dev/null; echo "$PWD"/"${0##*/}")"
PO=`dirname "$AP"`

RELEASES="intrepid jaunty karmic"

for dist in $RELEASES; do
  echo "Updating $dist..."
  $PO/mirror_$dist
done

```

This one should be even more evident. It's simply my "update all distributions" script and is a wrapper for the first script. This script also works perfectly when I run it myself.

Now here's my problem. I added a job to crontab using the command 'sudo crontab -e' and added the following line:

```

0 2 * * * /media/repositories/update.sh

```

Now here's the weird problem. When cron runs this script only the FIRST distribution (intrepid) is executed. The rest of them are not. I know this because the log file timestamps aren't getting updated and if I run the command manually there are little to no updates for intrepid but there are tons of updates for jaunty and karmic. Does anyone have any idea of why this is happening?

---

### Post by saulgoode on 2010-02-26
> **shaggy999 said:**
> This one should be even more evident. It's simply my "update all distributions" script and is a wrapper for the first script. This script also works perfectly when I run it myself.
Unless I'm missing something, *update.sh* is not really a "wrapper for the first script"; it appears to bypass *mirror_distro.sh* and invokes each of the *mirror_intrepid*, *mirror_jaunty*, and *mirror_karmic* scripts directly.

---

### Post by shaggy999 on 2010-02-26
I guess that's what I meant.

---

### Post by laceration on 2010-02-26
I wouldn't call it a bash problem. It is a cron problem.  I too have written bash scripts that work fine from the cli, but just do not work from cron.  Cron mysteriously can have problems executing a script from within a script.  It doesn't look this all needs to be in 2 scripts.  Combine into one and then try.
I have also broken tasks into multiple cron lines, when I have had this problem.

---

### Post by gmargo on 2010-02-26
Why have the complexity of distro differentiation based on symbolic link names?  I would pass an argument into the mirror_distro.sh script.

---

### Post by gmargo on 2010-02-26
Your scripts work for me.  I modified the mirror script to just echo the mirror commands instead of doing them, but it worked for the three distros from the command line and from cron.  On Hardy.

---

### Post by saulgoode on 2010-02-26
I use Dillon's CRON (rather the default CRON that ships with Debian), so I can't specifically help you; however, I would suggest investigating the ownership permissions of your symbolic links -- in particular the group permissions (CRON may be using SGID instead of SUID).

---

### Post by shaggy999 on 2010-02-26
> **gmargo said:**
> Your scripts work for me.  I modified the mirror script to just echo the mirror commands instead of doing them, but it worked for the three distros from the command line and from cron.  On Hardy.

Strangely enough that works for me as well, but the original script does not work. I find it really strange that it calls the first script, but not the second or third script. It really just boggles my mind because it obviously is capable of calling a second script from within itself.

As for why I am not using parameters to pass to a second script, the second script was more of an afterthought. I developed the first script based on another script that I had found elsewhere on the net and I thought it was fairly slick. I had separate cron jobs for each script but I ran into a problem where if I scheduled them too close together they would "run into" each other. Meaning one script would not be finished before the next one began. I wanted them to run sequentially. So I made a separate script that just called each of them in turn so that the entire repository update occurs as fast as possible without the scripts running into each other.

---

### Post by shaggy999 on 2010-02-26
> **saulgoode said:**
> I use Dillon's CRON (rather the default CRON that ships with Debian), so I can't specifically help you; however, I would suggest investigating the ownership permissions of your symbolic links -- in particular the group permissions (CRON may be using SGID instead of SUID).

```

drwxr-xr-x  8 root root 4.0K 2010-02-26 10:17 .
drwxr-xr-x 13 root root 4.0K 2010-02-26 10:24 ..
drwxr-xr-x  8 root root 4.0K 2009-09-15 22:15 intrepid
drwxr-xr-x 11 root root 4.0K 2009-07-12 22:22 jaunty
drwxr-xr-x  5 root root 4.0K 2009-10-30 00:14 karmic
drwx------  2 root root 4.0K 2009-12-27 20:14 lost+found
drwxr-xr-x  5 root root 4.0K 2010-02-17 11:07 lucid
-rwxr--r--  1 root root 2.7K 2010-02-19 22:38 mirror_distro.sh
lrwxrwxrwx  1 root root   16 2009-11-16 18:43 mirror_intrepid -> mirror_distro.sh
lrwxrwxrwx  1 root root   16 2009-11-16 18:43 mirror_jaunty -> mirror_distro.sh
lrwxrwxrwx  1 root root   16 2009-11-16 18:43 mirror_karmic -> mirror_distro.sh
lrwxrwxrwx  1 root root   16 2010-02-17 11:06 mirror_lucid -> mirror_distro.sh
drwxr-xr-x  2 root root 4.0K 2009-11-22 20:26 sources.list
-rwxr--r--  1 root root  207 2010-02-25 23:34 update.sh


```

Everything looks fine to me.

---

### Post by geirha on 2010-02-27
Turn on debugging by setting the -x option on the shell (change she-bang to «#!/bin/bash -x» or run «set -x» at the start of the script), and redirect the output to a file.

```
0 * * * * /media/repositories/update.sh >/tmp/update-output.log 2>&1
```

---

### Post by gmargo on 2010-02-27
Random thoughts, since I'm baffled:

[LIST]
[*]What happens if you run them in a different order, like with karmic first?
[*]You do have #!/bin/bash as the very first line, right?  (Making sure dash isn't used)
[*]Try set -x in both scripts and review the output.
[*]There's no reason to run these as root; I would use a regular user. But that shouldn't matter.
[*]You seem rather cavalier about quoting, which is most likely ok as long as none of the paths contain a space.  But I would quote the heck out of it.
[/LIST]

---

### Post by shaggy999 on 2010-02-27
> **geirha said:**
> Turn on debugging by setting the -x option on the shell (change she-bang to «#!/bin/bash -x» or run «set -x» at the start of the script), and redirect the output to a file.

```
0 * * * * /media/repositories/update.sh >/tmp/update-output.log 2>&1
```

This worked. Adding "-x" to the beginning of the mirror_distro.sh script works without even adding the log redirect to cron. If I remove the "-x" it stops working again. But I get no error message when I redirect to a log. It's like it silently fails. I am really baffled why that would happen. Oh well. Adding "-x" works.

---

### Post by geirha on 2010-02-28
> **shaggy999 said:**
> This worked. Adding "-x" to the beginning of the mirror_distro.sh script works without even adding the log redirect to cron. If I remove the "-x" it stops working again. But I get no error message when I redirect to a log. It's like it silently fails. I am really baffled why that would happen. Oh well. Adding "-x" works.

Indeed, that's very odd. I was hoping it would give an indication of what was wrong, not magically make it work.

---

