---
title: "SSH Environment"
date: 2011-03-14
forum: Programming Talk
---

### Post by Washdogg on 2011-03-14
So, I'm trying to write a couple of scripts at the moment, one to check if a process is running remotely on another machine, and another to copy a file from another computer.

Whilst this sounds trivial, and I have working scripts to achieve both these things, the scripts need to be run by another process which doesn't share my environment. 

In this example:
```
if ssh me@xxx ps ax | grep xbmc | grep -v grep 2>&1 > /dev/null
then
    f_LOG 'xbmc up on tv, updating...'
    curl --get "http://xxx/xbmcCmds/xbmcHttp?command=ExecBuiltIn&parameter=XBMC.updatelibrary(video)" 2>&1> /dev/null
else
    f_LOG 'I think xbmc is down on tv.'
fi

```

When run as me ./path_to_script from a terminal, the script happily logs into the remote server, finds the xbmc process and curls the appropriate page from XBMC, but when run from another process, say MythTV as a user job, the SSH commands fail because (I presume) MythTV doesn't share my environment. 

So what's the best way to solve this? I should probably add that I've set up keys etc. so entry of a password is not the issue.

Thanks!

---

