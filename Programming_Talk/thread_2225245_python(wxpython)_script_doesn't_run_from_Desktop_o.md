---
title: "python(wxpython) script doesn't run from Desktop or directory"
date: 2014-05-20
forum: Programming Talk
---

### Post by eightbits2010 on 2014-05-20
```
**bash: ./NewGasChkWIP.py: /usr/bin/env/python^M: bad interpreter: Not a directory**
```

When navigating to the directory which contains the py file I get the above error in the the terminal mode if
i use : ```
./NewGasChkWIP.py
```.
If I use instead ```
python NewGasChkWIP.py
``` , then the script executes just fine.



I have another script located on the Desktop. And when I click on that Icon, I get the prompt to run in the terminal or display. In the script that does work (not the same script, no GUI) it runs.

Thinking that it has something to do with the```
 import wx
``` I added that to the non GUI script and it still would run as before.

I have not a clue how to resolve this issue. If I could understand the before mentioned  error, then progress might be had.

---

### Post by steeldriver on 2014-05-20
The **^M** character suggests you copied the file from Windows and didn't fix the line terminations

```

bash: ./NewGasChkWIP.py: /usr/bin/env/python**^M**: bad interpreter: Not a directory

```

Run the script through dos2unix, or open it in vi/vim and do a set ff=unix, or use something like
```

sed -i 's/\r$//' NewGasChkWIP.py

```

to strip out the CRs

Also it should probably be

```

/usr/bin/env python

```

(with a space) NOT
```

/usr/bin/env/python

```

---

### Post by eightbits2010 on 2014-05-20
No, it was only generated on Ubuntu 12.04 using GEDIT. I used GHEX to examine the file contents
and it seems there is  0x0a and 0x0d at the end of that line. BTW, If I execute the script using IDEL,  it runs. I also attempted to erase anything at the end of the hashbang line while in IDEL. Then, after saving the file and closing IDEL I go back to the terminal mode, at the file's directory and attempt
 to run the script using ```
./NewGasChkWIP.py
```  but still get an error:
  ```
bash: ./NewGasChkWIP.py: /usr/bin/: bad interpreter: Permission denied
```
This error message is different ???
I have no idea how to define this issue for a resolution :-( 
 

 Is  GEDIT not suitable to write python code?
 I am pretty sure I used it for a couple of more python scripts.  

 Any suggestions on how to narrow this issue down to the editor?
 I am thinking that I can just use the GHEX editor and remove the CR/LF ?
 BTW, what should the hashbang line end with? Is it CR or LF?
 

 Thanks .

---

### Post by eightbits2010 on 2014-05-20
UPDATE: I used the ghex hex editor and removed the 0x0d and 0x0a (CR/LF) at the end of the hashbang line.  After saving the file, then I was able to execute from the Desktop by clicking the Icon associated with the script. It did work. Also, I could now use the ```
./filename.py
``` on the command line at the files directory and that works as well  

 Thanks for pointing me in the right direction.   If gedit is not going to handle the python hashbang line correctly, and I see no settings to accomplish this, then what is the better editor. I really don't want to have to stop what I am doing just to learn a new or different editor.  
 

 I suppose I could use the IDEL editor but have acclimated myself to using the  GEDIT editor.
 

 Is there someway to configure GEDIT to handle the hashbang issue?
 GEDIT does have a setting for python, but that doesn't seem to make any difference in this issue.

Thank you steeldriver, your assistance also helped me to get the GUI part working as well :D

---

### Post by steeldriver on 2014-05-20
Hmm... gedit works fine as a python script editor for me - perhaps there's something funny in your settings?

e.g. this file was created in gedit - using 'cat -net' we can see it has proper LF line endings
```

$ cat -net geditshebang.py
     1    #!/usr/bin/env python$
     2    $
     3    import sys$
     4    $
     5    print sys.version$
     6    $

```

and it runs fine
```

$ ./geditshebang.py 
2.7.3 (default, Feb 27 2014, 20:00:17) 
[GCC 4.6.3]

```

Anyhow glad you got it fixed

---

### Post by eightbits2010 on 2014-05-20
Yes, glad it works too! I will continue to research this as I want to use gedit. But, I don't see any settings to change that.
In the morning I will see if adding a space after the hashbang will work.
I too am surprised that gedit places the CR/LF in the file.
If I see any thing worth noting I will post to this thread.

---

