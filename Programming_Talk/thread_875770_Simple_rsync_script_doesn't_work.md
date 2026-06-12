---
title: "Simple rsync script doesn't work"
date: 2008-07-31
forum: Programming Talk
---

### Post by NoDude on 2008-07-31
I've written this small script to deploy my local dev folder to the live server, but when I run it I get "rsync: -p9999': unknown option". I tried quoting and escaping the quotes around the -e option in every way I could think of, but it still doesn't work. Any ideas?

```

REMOTE_SERVER='user@site.com';
REMOTE_PATH='vhosts/site.com/httpdocs/'
LOCAL_DIR='/var/www/site/'

MISC_OPTIONS="--progress -vrae 'ssh -p9999' $1";
EXCLUDE_OPTIONS='--exclude=*config* --exclude=*.svn* --exclude=*log* --exclude=*jpg --exclude=_cache/*';

RSYNC_COMMAND="rsync $EXCLUDE_OPTIONS $MISC_OPTIONS $LOCAL_DIR $REMOTE_SERVER::$REMOTE_PATH";

echo -n "Do you want to proceed synching $REMOTE_SERVER (additional options \"$1\") (y/n)? "
read -e PROCEED

if [ $PROCEED = 'y' ];
then
  echo -n "Compiled command is \"$RSYNC_COMMAND\", proceed (y/n)? "
  read -e PROCEED2

  if [ $PROCEED2 = 'y' ];
  then
    $RSYNC_COMMAND
  fi
fi

```

Edit: the solution is to put eval in front of the final $RSYNC_COMMAND in order to evaluate the inner quotes of the -e option.

---

