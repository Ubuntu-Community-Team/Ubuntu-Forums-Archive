---
title: "Auto make c++ in gedit"
date: 2007-05-05
forum: Programming Talk
---

### Post by lognok on 2007-05-05
Hi there,
  I have enabled the 'external tools' plugin in gedit, because I wish to use external commands to auto make/build (don't know the difference...) a c++ file (helloworld.cpp). This is the command I give:

g++ $GEDIT_CURRENT_DOCUMENT_PATH -o $GEDIT_CURRENT_DOCUMENT_NAME

The problem is that my helloworld.cpp file is overwritten and changes to an executable file.

Question:
How do I get gedit to do: g++ <filemane>.<extension> -o <filename> ?

Thank for any help.

---

### Post by wtruong on 2007-05-05
its g++ -o outfile infile

---

### Post by lognok on 2007-05-05
'g++ -o outfile infile'  and  'g++ infile -o outfile' produces the same result, which is outfile.

Problem is I can't get outfile without an extension, it always gives me ex. helloworld.cpp instead of helloworld.

---

### Post by WW on 2007-05-05
From [this web page]("http://live.gnome.org/Gedit/ToolLauncherPlugin"), it appears that the plugin does not provide an environment variable for the 'root' of the file name (i.e. the file name without an extension).

Here is a quick hack that you can use for your g++ command:
```

g++ $GEDIT_CURRENT_DOCUMENT_NAME -o `echo $GEDIT_CURRENT_DOCUMENT_NAME | sed "s/\(.*\)\.cpp$/\1/"`

```
It assumes that the extension is '.cpp'.

---

### Post by lognok on 2007-05-05
Dude, that is just sweet :) 

It works great, thank you.

---

### Post by hod139 on 2007-05-05
For a bash only hack, you can do
```

echo g++ $GEDIT_CURRENT_DOCUMENT_NAME -o ${GEDIT_CURRENT_DOCUMENT_NAME%.*}

```

---

### Post by WW on 2007-05-05
Cool.  That's *much* nicer than my ugly hack.

---

### Post by lognok on 2007-05-06
Thanks goes out to WW and hod139.

I can now compile and run my c++ code with accelerators in gedit with these commands in the 'external tools' plugin:

Compile:
    g++ $GEDIT_CURRENT_DOCUMENT_NAME -o ${GEDIT_CURRENT_DOCUMENT_NAME%.*}

Run:
    ./${GEDIT_CURRENT_DOCUMENT_NAME%.*}

I think gedit + 'external tools' is a nice combination for my learning c++ coding. IDE's may come in handy when I begin to write larger projects, but for now this nice and simple.

Long live UbuntuForums!!!!!!!
:guitar:

---

### Post by JuhaPoy on 2008-10-08
> **lognok said:**
> 

Run:
    ./${GEDIT_CURRENT_DOCUMENT_NAME%.*}



Run in terminal screen:
[INDENT]gnome-terminal -x ./${GEDIT_CURRENT_DOCUMENT_NAME%.*} --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR &[/INDENT]

Did anyone know how to add 'breakpoint'.

---

