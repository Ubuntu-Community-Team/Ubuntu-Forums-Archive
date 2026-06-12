---
title: "Multi-Grep at One Time"
date: 2010-10-16
forum: Programming Talk
---

### Post by huangyingw on 2010-10-16
Hello,
     I am a newbie at Linux c++ programming, I had difficulty at reading mass of codes.
     So, I would like to write a shell, which could find in code files(like *.cc,*.py,*.h,etc), and filter out the comment lines(which begin with //, or #), and finally find my desired key word, so I try this shell,
```
    find "$1" \( -name \.svn -o -name \.git -o -name \.hg \) -prune -o \( -name \*\.c -o -
name \*\.cc -o -name \*\.h -o -name \*\.sh -o -name \*\.py -o -name YBUILD -o -name [m,M]a
kefile \) -exec grep "^\s*[^# //\t].*$"  {} \; |grep -wnH  "$2"

```
    But the above one's fault is that , it is output is like this:```
(standard input):22878:int main(int argc, char **argv) {
```, which might be meaningless for me.
    I want to combine the two condition at one grep, like bellow ```
   find "$1" \( -name \.svn -o -name \.git -o -name \.hg \) -prune -o \( -name \*\.c -o -na
 me \*\.cc -o -name \*\.h -o -name \*\.sh -o -name \*\.py -o -name YBUILD -o -name [m,M]ake
 file \) -exec grep -wnH "\(^\s*[^# //\t].*$\)|\("$2"\)"  {} \; 

```
    But, after this change, I got no result:(:(..

---

