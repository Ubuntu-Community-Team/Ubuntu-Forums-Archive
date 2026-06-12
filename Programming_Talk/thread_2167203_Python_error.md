---
title: "Python error"
date: 2013-08-12
forum: Programming Talk
---

### Post by wingnut2626 on 2013-08-12
def main():
  args = sys.argv[1:]
  if not args:
    print "usage: [--todir dir][--tozip zipfile] dir [dir ...]";
    sys.exit(1)

  
    **elif args[0] == '--todir':**
        todir = args[1]
        del args[0:2]
        if args:
            destination = args[0]
            copytodir(todir, destination)
        else:
        print 'error, closing.'
        sys.exit(1)

In my IDE the bold line conforms to the indent, but how come here it does not?   and when I try to run it I get an unexpected indent Traceback?

---

### Post by wingnut2626 on 2013-08-12
<CODE>

def main():
  args = sys.argv[1:]
  if not args:
    print "usage: [--todir dir][--tozip zipfile] dir [dir ...]";
    sys.exit(1)

  
   ** elif args[0] == '--todir':**
        todir = args[1]
        del args[0:2]
        if args:
            destination = args[0]
            copytodir(todir, destination)
        else:
        print 'error, closing.'
        sys.exit(1)
</CODE>

should be more like it

---

### Post by wingnut2626 on 2013-08-12
grrr now i cant even post code correctly.....

---

### Post by Cheesemill on 2013-08-12
You need to use [NOPARSE]```
   
```[/NOPARSE] tags to put a block of code in your post :)

---

### Post by wingnut2626 on 2013-08-12
LOL I figured it out.  For some reason geany and gedit were showing the code as properly edited.  When I opened the code in kate and nano, it showed me where the indentation was off.  I think it will be kate for me in the long haul.

---

### Post by Vaphell on 2013-08-12
This happens when you mix spaces and tabs - visually the same, logically not so much. Personally i set gedit to replace tabs with 2 spaces.

---

