---
title: "PYTHONPATH does not overwrite"
date: 2015-07-07
forum: New to Ubuntu
---

### Post by obergam on 2015-07-07
Hello, 

I am trying to setup my ubuntu box to use for selenium webdriver and write automation scripts. I am following instructions to overwrite PYTHONPATH :

9) Open the terminal and overwrite the PYTHONPATH by running the following commands: 
a) echo -e '# Overwrite PYTHONPATH\nexport PYTHONPATH=/home/YOUR_HOME_HERE/Desktop:$PYTHONPATH' | tee ?a ~/.bashrc 
b) echo -e '# Overwrite PYTHONPATH\nexport PYTHONPATH=/home/YOUR_HOME_HERE/Desktop:$PYTHONPATH' | tee ?a ~/.profile

(with 'YOUR_HOME_HERE' being my home folder)

Then, as directed I check if the desktop has been added to the PYTHONPATH:
python
import sys
sys.path

My desktop does not get added to pythonpath. Is there a problem with the script?

Thank you in advance

---

### Post by ian-weisser on 2015-07-07
> **obergam said:**
> 
9) Open the terminal and overwrite the PYTHONPATH by running the following commands: 
a) echo -e '# Overwrite PYTHONPATH\nexport PYTHONPATH=/home/YOUR_HOME_HERE/Desktop:$PYTHONPATH' | tee ?a ~/.bashrc 
b) echo -e '# Overwrite PYTHONPATH\nexport PYTHONPATH=/home/YOUR_HOME_HERE/Desktop:$PYTHONPATH' | tee ?a ~/.profile
...
My desktop does not get added to pythonpath. Is there a problem with the script?

Step 9 won't work for several reasons, none of which are your fault.
Could you please provide the link to those instructions?

Generally, you should not need to *overwrite* Python's sys.path; that would cause lots of problems. Most well-written software installs to a location already in sys.path. Even my hacky scripts append to  (instead of overwriting) sys.path when they need to add a new location

---

### Post by Habitual on 2015-07-08
I think I'm seeing [double]("http://ubuntuforums.org/showthread.php?t=2283912&p=13310194#post13310194")? 
I also thought you fixed this? ;)

---

### Post by obergam on 2015-07-08
The instructions were from Udemy.com. You would need a login and a password, but I dowloaded the PDF with the instructions. (Attached)

---

### Post by obergam on 2015-07-08
This is a different issue, yet with the same script. The original issue was my mistake because I think I did not change the home directory. Here, I am just trying to add my desktop to the pythonpath as directed in the instructions. :cry:

---

### Post by sandyd on 2015-07-08
```

echo -e '# Overwrite PYTHONPATH\nexport PYTHONPATH=$HOME/Desktop:$PYTHONPATH' >> ~/.bashrc
echo -e '# Overwrite PYTHONPATH\nexport PYTHONPATH=$HOME/Desktop:$PYTHONPATH' >> ~/.profile
source ~/.bashrc

```

Side note: Ubuntu does not have a PYTHONPATH env variable by default. As a result, the PYTHONPATH gets set to something like
```

/home/user/Desktop:
```
With an extra colon.

If that is not intended behavour, run the following instead:
```

echo -e '# Overwrite PYTHONPATH\nexport PYTHONPATH=$HOME/Desktop' >> ~/.bashrc
echo -e '# Overwrite PYTHONPATH\nexport PYTHONPATH=$HOME/Desktop' >> ~/.profile
source ~/.bashrc

```

---

