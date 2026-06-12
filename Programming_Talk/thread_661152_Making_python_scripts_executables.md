---
title: "Making python scripts executables"
date: 2008-01-07
forum: Programming Talk
---

### Post by Mr.popo on 2008-01-07
Im having a problem. I may have posted before on help on this part of python but i still dont undertstand.I am sick of using a problem such as dr python or geany which when you execute the program a script is made along with the python script which alows it to execute. Well anyway i want to be able to use gedit and then execute the script.I have tryed adding these lines:

Which one should work?
```

#!/usr/bin/python
def main():
	print "main"
main()

```

```

#!/usr/bin/python2.5
def main():
	print "main"
main()

```

If this line of code worked then I would expect to just double click the python scripts and hope it runs in a terminal.

How could i fix this?


thankyou
Mr.popo :)

---

### Post by Peyton on 2008-01-07
In the terminal, you can either run:
> python scriptName.py
Or you can run:
> chmod u+x # do this once
./scriptName.py

---

### Post by Mr.popo on 2008-01-07
Thanks.

---

### Post by Acglaphotis on 2008-01-07
I think it's better to use "/usr/bin/env python" instead of "#!/usr/bin/python", it helps prevents uncompatibilities with other distros.

---

### Post by evymetal on 2008-01-08
to get it to run from a double click you have to right click and select "allow execution of this file" (or something similar) - I think this is just a gui way of doing chmod though.

ps I would personally keep the 
#!/usr/bin/python2.5
if you are doing anything that specifically requires python 2.5 - python tends to break quite a bit between releases and I have several versions of python installed.

---

