---
title: "[Python] Config Parser problem"
date: 2009-05-22
forum: Programming Talk
---

### Post by Pyro.699 on 2009-05-22
Hello,

I'm using the ConfigParser to read from and write to a configuration file.

Here is the basic structure of what I'm trying...

```

config_file = open('./config/config.ini', 'a+')
config = ConfigParser.ConfigParser()
config.readfp(config_file)
config.write(config_file)

```

It seems redundant, but its to try and get it working, when i have that i get this error

> 
Traceback (most recent call last):
  File "C:\Documents and Settings\Cody\Desktop\pythontest\pytest.py", line 14, in <module>
    config.write(config_file)
  File "C:\Python25\lib\ConfigParser.py", line 369, in write
    fp.write("[%s]\n" % section)
IOError: [Errno 0] Error


I have tried everything and seem to be able to only do one of either read from the file and not be able to write, and if im able to read from the file, im not able to read it; also when i write to it it deletes all information inside the file.

More examples...

```

config_file = open('./config/config.ini', 'a+')
config = ConfigParser.ConfigParser()
config.readfp(config_file)
print config.get("[Master]", "username")
config.write(config_file)

```

Here was whats in the ini file:
[quote=/config/config.ini]
[Master]
username = Pyro.699
[/quote]

> 
Traceback (most recent call last):
  File "C:\Documents and Settings\Cody\Desktop\pythontest\pytest.py", line 14, in <module>
    print config.get("[Master]", "username")
  File "C:\Python25\lib\ConfigParser.py", line 511, in get
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: '[Master]'



Any help is greatly appreciated
Thanks
~Cody Woolaver

---

### Post by slavik on 2009-05-22
my guess is that when it reads it, it doesn't close the file, hence you can't write to it. try looking for something that tells config module to close file.

edit: why aren't you looking into the code for it?

---

### Post by Pyro.699 on 2009-05-22
Well, I'snt ConfigParser developed by the python community? I'm assuming that I'm doing something wrong (usually am) and i figured that if anyone knew how to solve the problem, it would be you guys. I searched **IOError: [Errno 0] Error** and it returned no useful results.

Any other sugguestions? I was thinking that maybe it was the mode

---

### Post by simeon87 on 2009-05-22
First of all, you should just specify the name of the section without the [ and ].

Second, I'm not sure if this is needed but perhaps you need to specify the full path; for example, I'm using:

```
CONFIG_FILE_LOCATION = os.path.expanduser("~/.appname/config.ini")
```

And then:

```

parser = ConfigParser.RawConfigParser()
parser.read(CONFIG_FILE_LOCATION)

```

---

### Post by smartbei on 2009-05-22
Your first example works for me - what it does is double the content of the config file - if it looked like this before:
```

[SEC1]
opt1 = val1

```
It looks like this afterwards:
```

[SEC1]
opt1 = val1
[SEC1]
opt1 = val1

```
Your second example (the one with getting the value given the section and option name), doesn't work because you are not supposed to pass the square brackets as part of the section name. Use this instead:
```

config.get("Master", "username")

```


I have a hunch that the problem your are experiancing with both reading and writing is a windows bug, since on Ubuntu here it is working fine.

@simeon87: It doesn't look like the problem is the path to the file, because then the 'open' would have failed and not the config parser.

---

