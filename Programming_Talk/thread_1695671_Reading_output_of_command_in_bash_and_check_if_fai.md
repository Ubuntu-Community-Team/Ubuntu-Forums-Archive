---
title: "Reading output of command in bash and check if failed."
date: 2011-02-26
forum: Programming Talk
---

### Post by carelburger on 2011-02-26
Hi,

I have a bash script that I wrote and it calls flexget which then give an output like this:


```
2011-02-26 15:11 INFO     feed          MyTracker       Produced 1 entries.
2011-02-26 15:11 INFO     feed          MyTracker       Accepted: 1 (Rejected: 0 Undecided: 0 Failed: 0)
2011-02-26 15:11 INFO     download      MyTracker       Downloading: Test
2011-02-26 15:11 INFO     modify_trackers MyTracker       Added http://test.net/announce.php?passkey=714c390d9916a735964c0a7ba7b6aa3d tracker to Test
2011-02-26 15:11 INFO     deluge        MyTracker       Connecting to daemon at localhost:58846..
2011-02-26 15:11 INFO     deluge        MyTracker       Connected to daemon at localhost:58846..
2011-02-26 15:11 INFO     deluge        MyTracker       Test successfully added to deluge.
2011-02-26 15:11 INFO     deluge        MyTracker       Connection lost to daemon at localhost:58846 reason: Connection was closed cleanly.
```

Ok so there it was successfull, but if not it would say failed.

The command looks like this:

```
flexget --feed=MyTracker --inject "$filename" "$HTTPDownloadLocation$filenameWithoutSpaces$TorrentExtension" --cli-config "path=$directory"
```

How can I pipe this output from flexget and look at the output and determine if it was successfull or a failure. I need to run different commands with a if statement depending on the success of the command.

---

### Post by johnl on 2011-02-26
Hi,

Most programs will return 0 on success or non-zero on failure.  This is stored in the special variable $?

You can check like this:

```

flexget --feed=MyTracker --inject "$filename" "$HTTPDownloadLocation$filenameWithoutSpaces$TorrentExtension" --cli-config "path=$directory"
RESULT=$?

if [ $RESULT -ne 0 ]; then
    echo "flexget failed with code $RESULT"
fi

```

alternatively, flexget may not do this (some programs don't).  In this case you can use grep - q and look for a certain string in the output.  For example, if when the command fails it prints "failure" to standard out, you can do something like this:

```

flexget --feed=MyTracker --inject "$filename" "$HTTPDownloadLocation$filenameWithoutSpaces$TorrentExtension" --cli-config "path=$directory"| grep -q "failure"

RESULT=$?   # grep will return 0 if it finds 'failure',  non-zero if it didn't

if [ $RESULT -eq 0 ]; then
    echo "flexget failed with code $RESULT"
fi

```

hope this helps.

---

