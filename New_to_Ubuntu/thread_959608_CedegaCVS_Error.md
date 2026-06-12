---
title: "CedegaCVS Error"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by bakentake on 2008-10-26
I have been trying to compile the CVS version of Cedega through:

[https://help.ubuntu.com/community/Cedega](https://help.ubuntu.com/community/Cedega)
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS)

I got to step 3 on the second link then my terminal gave me:

```

--------- Error log - file /home/zach/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/zach/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

```

The line its looking for looks like:
```
if cvs -d $CVSroot $CVSoptions $CVSmode $CVSCheckOutDir >"$ErrorLogFile" 2>&1
```

Any help would be appreciated, I have no clue what to do...

---

