---
title: "Zenity Progress Box"
date: 2008-08-11
forum: Programming Talk
---

### Post by jfreak53 on 2008-08-11
Ok I've searched all over the net and cannot find any inclusive information regarding this subject.  Some people say that you can encapsulate the zenity cancel button others say no.  But I can never find any code for it if it's possible, so let's come to the source. haha

All I want to do is encapsulate the zenity cancel button on a progress window.  This is the code that I'm using in a script file:

```
ffmpeg -i "$File" -s $size -b $compression -vcodec wmv2 -ar 44100 -ab 56000 -ac 2 -y "$final".wmv 2>&1 | zenity --progress --title "FLV to WMV" --text "Converting: $File" --pulsate --auto-close
```

All the code works fine and it auto quits when it's done.  All I want to do is that when someone clicks on cancel it kills ffmpeg and closes the window.  Is this possible with Zenity?

Thanks in advance.

---

### Post by ConMan318 on 2008-08-11
I don't know if this will help, but with Perl, if the user clicks 'cancel' in a Zenity window, a non-zero value is stored in the variable $?.  So in Perl, after the code for the dialog box you would write something like "exit if $?", which would exit the program if the user clicked cancel.

I assume, since Perl has to get that variable from the operating system, that Bash also contains such a variable to show whether a dialog box was completed successfully.

My guess is that if you set the code for the Zenity window equal to a variable, it will store a boolean value into that variable depending on the method of closure.  Most likely it will store a zero if the window auto-closed and a non-zero number (likely this value would be 1) if the user clicked cancel.

Then you would just have to code an exit function based on that value.



EDIT:

From the zenity man page:
```

       zenity  is a program that will display GTK+ dialogs, and return (either
       in the return code, or on standard output) the users input. This allows
       you to present information, and ask for information from the user, from
       all manner of shell scripts.

       For example, zenity --question will return either 0 or 1, depending  on
       whether  the  user  pressed OK or Cancel. zenity --entry will output on
       standard output what the user typed into the text entry field.

```

I'm sure the progress window does something similar.  I'll leave the specifics up to you.

---

