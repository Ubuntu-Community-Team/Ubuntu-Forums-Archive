---
title: "ftp shell script issue"
date: 2006-09-18
forum: Programming Talk
---

### Post by closet geek on 2006-09-18
Hi,

Why on earth does this code end up placing the file above the public_html direcory:

ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
cd public_html
put $FILE
quit
END_SCRIPT
exit 0

it definitely changed to public_html (as confirmed by pwd). Yet it *always* puts the file above the public_html.

Help!

cg

---

### Post by closet geek on 2006-09-20
This was due to my $FILE variable being of the form '/file' which caused the FTP client to navigate to root.

cg

---

