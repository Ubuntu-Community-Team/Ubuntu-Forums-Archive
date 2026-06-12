---
title: "BASH heredoc help"
date: 2012-05-21
forum: Programming Talk
---

### Post by hantechbl on 2012-05-21
I've finished a script, however I seem to have major issues with heredocs, I have no idea why this doesn't work, I have seen numerous guides using the same thing, this is just a snippet of the whole script that appears to be the source of the errors when executing the script.  When I put a # before the FTP line, all of the syntax errors go away.

```
function upload () {
    local file="$1"
    log INFO Upload Starting
    ftp -n $bip <<End-Of-Session
    quote USER $bsuser
    quote PASS $bspassword
    cd $finaldir
    put $file
    bye
    End-Of-Session
    log INFO Upload Done
}
```

---

### Post by diesch on 2012-05-21
The end mark of the here-doc has to be the only thing in the line, without any heading or trailing spaces, like

```
function upload () {
    local file="$1"
    log INFO Upload Starting
    ftp -n $bip <<End-Of-Session
    quote USER $bsuser
    quote PASS $bspassword
    cd $finaldir
    put $file
    bye
End-Of-Session
    log INFO Upload Done
}
```

---

### Post by hantechbl on 2012-05-22
Thanks, Problem solved.

---

