---
title: "How add a header logo to my terminal?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-10-26
Hello, there is a way to put a logo like this in my terminal everytime i open it? or something like an ascii text with my name!!!! 

Thanks

---

### Post by cyfur01 on 2008-10-26
Depends on if you want it to do this for just you or all users.

For just you, edit ~/.bashrc
For everyone, edit /etc/bash.bashrc

You can then add the print statement to the end of either of the above files by adding a line like:
```

echo "Logged $USER in!"

```
This is just a very basic shell command, and the possible variables (like $USER) will be all the ones printed it you type "env" into a terminal. The above statement would then print "Logged your_user_name in! every time you launch a new terminal.

The alternative thing to do would be to put the message in a text file and then cat (print) the contents of that file with a command like
```

cat /path/to/txt_file

```This would be in place of the aforementioned echo command, although this option will not allow you to use shell variables. If you want both, you can use a combination of both of these commands.

---

### Post by billgoldberg on 2008-10-26
Try this:

[http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/](http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/)

---

