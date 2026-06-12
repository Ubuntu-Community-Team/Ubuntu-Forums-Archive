---
title: "redirect console output"
date: 2005-10-15
forum: Programming Talk
---

### Post by c2483 on 2005-10-15
Does anyone know how I can redirect the console output to a python gui widget.

For example, say I want to have a gui with a button and a textbox.  I know how to do the gui.
When the button is clicked, I want to display the output from cat /proc/cpuinfo or something in the textbox.

Is this possible?

---

### Post by adwait on 2005-10-15
I am not really sure if there is a proper way to do this.......but when I wanted to do the same with c++, couldn't find anything. But you can just execute
```
cat /proc/cpuinfo >> <filename> 
```

and then open that file with your program.

---

### Post by c2483 on 2005-10-16
yeah, that's what i thought, thanks 

if anyone else knows, please post

---

### Post by thumper on 2005-10-16
You don't need to redirect to a file, just open the file from the proc filesystem as such:
```
Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> f = open('/proc/cpuinfo')
>>> l = f.readlines()
>>> f.close()
>>> l
['processor\t: 0\n', 'vendor_id\t: GenuineIntel\n', 'cpu family\t: 15\n', 'model\t\t: 2\n', 'model name\t: Intel(R) Pentium(R) 4 CPU 2.80GHz\n', 'stepping\t: 5\n', 'cpu MHz\t\t: 2806.948\n', 'cache size\t: 512 KB\n', 'fdiv_bug\t: no\n', 'hlt_bug\t\t: no\n', 'f00f_bug\t: no\n', 'coma_bug\t: no\n', 'fpu\t\t: yes\n', 'fpu_exception\t: yes\n', 'cpuid level\t: 2\n', 'wp\t\t: yes\n', 'flags\t\t: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr\n', 'bogomips\t: 5554.17\n', '\n', 'processor\t: 1\n', 'vendor_id\t: GenuineIntel\n', 'cpu family\t: 15\n', 'model\t\t: 2\n', 'model name\t: Intel(R) Pentium(R) 4 CPU 2.80GHz\n', 'stepping\t: 5\n', 'cpu MHz\t\t: 2806.948\n', 'cache size\t: 512 KB\n', 'fdiv_bug\t: no\n', 'hlt_bug\t\t: no\n', 'f00f_bug\t: no\n', 'coma_bug\t: no\n', 'fpu\t\t: yes\n', 'fpu_exception\t: yes\n', 'cpuid level\t: 2\n', 'wp\t\t: yes\n', 'flags\t\t: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr\n', 'bogomips\t: 5603.32\n', '\n']
>>>

```

---

### Post by wmcbrine on 2005-10-17
Yeah, bad example, since that's a file already anyway. (That's the beauty of Unix: *everything* is a file.) But for the general case of capturing the output of a program you've launched, you can use popen() ,in place of system() or exec(). Equivalently, but on a different level, you can link the output of any program to the input of any other program that can read from a file, via named pipes. (If the program can read standard input, you can use regular pipes.) Check out the "mkfifo" command.

---

