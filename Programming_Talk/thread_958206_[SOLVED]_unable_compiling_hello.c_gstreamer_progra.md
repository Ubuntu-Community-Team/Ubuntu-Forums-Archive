---
title: "[SOLVED] unable compiling hello.c gstreamer program.."
date: 2008-10-25
forum: Programming Talk
---

### Post by kcode on 2008-10-25
I'm unable to compile this program:

```

#include <gst/gst.h>

int
main (int   argc,
      char *argv[])
{
  const gchar *nano_str;
  guint major, minor, micro, nano;
  gst_init (&argc, &argv);
  gst_version (&major, &minor, &micro, &nano);
  if (nano == 1)
    nano_str = "(CVS)";
  else if (nano == 2)
    nano_str = "(Prerelease)";
  else
    nano_str = "";
  printf ("This program is linked against GStreamer %d.%d.%d %s\n",
          major, minor, micro, nano_str);
  return 0;
}

```

with following error:

```

 gcc -Wall $(pkg-config --cflags --libs gstreamer-0.10.21) hello.c -o hello
Package gstreamer-0.10.21 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gstreamer-0.10.21.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gstreamer-0.10.21' found
hello.c:1:21: error: gst/gst.h: No such file or directory
hello.c: In function &#8216;main&#8217;:
hello.c:7: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
hello.c:7: error: &#8216;nano_str&#8217; undeclared (first use in this function)
hello.c:7: error: (Each undeclared identifier is reported only once
hello.c:7: error: for each function it appears in.)
hello.c:8: error: &#8216;guint&#8217; undeclared (first use in this function)
hello.c:8: error: expected &#8216;;&#8217; before &#8216;major&#8217;
hello.c:10: error: &#8216;major&#8217; undeclared (first use in this function)
hello.c:10: error: &#8216;minor&#8217; undeclared (first use in this function)
hello.c:10: error: &#8216;micro&#8217; undeclared (first use in this function)
hello.c:10: error: &#8216;nano&#8217; undeclared (first use in this function)
hello.c:17: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

```

i installed gstreamer-0.10.21 manually in my home directory.
i also did:
export PKG_CONFIG_PATH=$PKGCONFIG:$libdir/pkgconfig

link i used:
used:[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/section-helloworld-compilerun.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/section-helloworld-compilerun.html) 

thanks

---

### Post by nvteighen on 2008-10-25
Well, several things.
0. Code tags in this forums are [ code ] [ /code ] (without spaces).

1. You're using the wrong compile command. You're referring to a 'gstreamer-0.10.21' pkg-config file that simply doesn't exist. It is 'gstreamer-0.10', as the documentation correctly states.

So, the compiling command would be:
```

gcc hello.c -o hello -Wall `pkg-config --cflags --libs gstreamer-0.10`

```

Note that I'm using backticks (`) not single-quotes (')! I'm not sure whether $(pkg-config...) is the same or not, but the usual way for using pkg-config is the one I describe.

2. I've refactored your code a little bit. In C you better always initialize variables... specially pointers!! And you forgot to #include <stdio.h> (for printf()).

```
[color=#BC7A00]#include <gst/gst.h>
#include <stdio.h>
[/color]
[color=#B00040]int[/color] [color=#0000FF]main[/color] ([color=#B00040]int[/color] argc, [color=#B00040]char[/color] [color=#666666]*[/color]argv[])
{
    [color=#408080][i]/* Always initialize stuff. You're never sure what value will the variable
     * take! */[/i][/color]

    gchar [color=#666666]*[/color]nano_str [color=#666666]=[/color] [color=#008000]NULL[/color]; [color=#408080][i]/* No longer const otherwise you won't be able to
                             * modify it. */[/i][/color]
    guint major [color=#666666]=[/color] [color=#666666]0[/color];
    guint minor [color=#666666]=[/color] [color=#666666]0[/color]; 
    guint micro [color=#666666]=[/color] [color=#666666]0[/color]; 
    guint nano [color=#666666]=[/color] [color=#666666]0[/color];

    gst_init ([color=#666666]&[/color]argc, [color=#666666]&[/color]argv);
    gst_version ([color=#666666]&[/color]major, [color=#666666]&[/color]minor, [color=#666666]&[/color]micro, [color=#666666]&[/color]nano);
    [color=#008000]**if**[/color] (nano [color=#666666]==[/color] [color=#666666]1[/color])
        nano_str [color=#666666]=[/color] [color=#BA2121]"(CVS)"[/color];
    [color=#008000]**else**[/color] [color=#008000]**if**[/color] (nano [color=#666666]==[/color] [color=#666666]2[/color])
        nano_str [color=#666666]=[/color] [color=#BA2121]"(Prerelease)"[/color];
    [color=#008000]**else**[/color]
        nano_str [color=#666666]=[/color] [color=#BA2121]""[/color];

    printf ([color=#BA2121]"This program is linked against GStreamer %d.%d.%d %s[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color],
            major, minor, micro, nano_str);
    [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

---

### Post by kcode on 2008-10-25
no success:(
1. i used gstreamer-0.10.21 as i installed this version
2. it also says guint is undeclared first use in this func.
3. tried backticks --> no success

---

### Post by nvteighen on 2008-10-25
> **kcode said:**
> no success:(
1. i used gstreamer-0.10.21 as i installed this version
2. it also says guint is undeclared first use in this func.
3. tried backticks --> no success

Just a question, where have you installed this from? I installed the 'libgstreamer0.10-dev' package from the repos and it worked.

---

### Post by kcode on 2008-10-25
thanks a lot 
it worked.
I installed it manually from the package downloaded from there website.
(you made my day!)
thanks again!

---

### Post by hnkulkarni on 2009-10-29
Hi , 
Thanks a lot for this post. 
I worked for me too..

But when we take the program to one step further , say I have to make a Qt GUI which will 
pop up a window showing the version with which this GStreamer is linked with.

Then I gain get the same errors 
error: gst/gst.h No such file or directory.

Can you please tell me how can I integrate GStreamer with Qt.

Thanking  you all in advance.

---

### Post by Zugzwang on 2009-10-29
> **hnkulkarni said:**
> Can you please tell me how can I integrate GStreamer with Qt.


So first of all install the development package mentioned above. The furter steps depend on the build system you are actually using. Which one is it? QMake? Then you can add the line "PKGCONFIG += gstreamer-0.10" to your solution (".pro") file.

---

### Post by zahidul_haque on 2011-06-05
Hi All,

I am new to UBUNTU. I installed Ubuntu10.10 and tried running the gstreamer example.
I wrote simple gstreamer example with C flavour only like

#include <gst/gst.h>
#include <glib.h>

int main() {
    g_print("Hello! World \n");
}

but I am getting compiler error "streamer.c:1: fatal error: gst/gst.h: No such file or directory
compilation terminated."

These header files are at

[B]/usr/include/glib-2.0/glib.h
[/B]
**/usr/include/****gstreamer-0.10/gst/gst.h**

Does anyone has an idea how to resolve this. Thanks in advance

Regards,
Zahid

---

