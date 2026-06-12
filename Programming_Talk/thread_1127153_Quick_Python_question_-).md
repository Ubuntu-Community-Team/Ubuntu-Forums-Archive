---
title: "Quick Python question :-)"
date: 2009-04-16
forum: Programming Talk
---

### Post by thirddeep on 2009-04-16
I have this little script, that works just fine.  Part of it looks like this :

```
if options.disk_boot == "GROW":
        options.disk_boot = "--size 1 --grow"
if options.disk_swap == "GROW":
        options.disk_swap = "--size 1 --grow"
if options.disk_root == "GROW":
        options.disk_root = "--size 1 --grow"
if options.disk_tmp == "GROW":
        options.disk_tmp = "--size 1 --grow"
if options.disk_usr == "GROW":
        options.disk_usr = "--size 1 --grow"
if options.disk_var == "GROW":
        options.disk_usr = "--size 1 --grow"
if options.disk_home == "GROW":
        options.disk_home = "--size 1 --grow"
```

and : 

```
if options.disk_tmp != "0":
        PARTITION_SIZES = PARTITION_SIZES + "logvol /tmp --fstype ext3 --vgname=LogVol01 --size=%s --name=tmp\n" % (options.disk_tmp)
if options.disk_usr != "0":
        PARTITION_SIZES = PARTITION_SIZES + "logvol /usr --fstype ext3 --vgname=LogVol01 --size=%s --name=usr\n" % (options.disk_usr)
if options.disk_var != "0":
        PARTITION_SIZES = PARTITION_SIZES + "logvol /var --fstype ext3 --vgname=LogVol01 --size=%s --name=var\n" % (options.disk_var)
if options.disk_home != "0":
        PARTITION_SIZES = PARTITION_SIZES + "logvol /home --fstype ext3 --vgname=LogVol01 --size=%s --name=home\n" % (options.disk_home)
```

I just _know_ there is a better way to do this than a bunch of if's.  But unfortunately I don't know what.

Could someone enlighten me please :-)

Thd.

---

### Post by Tony Flury on 2009-04-16
Instead of putting the values into variables - why not use a dictionary, where the key is one of "boot", "root", "swap", "tmp" etc ....

your ifs could be then replaced with a loop that itetrates around the dictionary, testing and setting the value for each key.

---

### Post by thirddeep on 2009-04-16
Right, I have :

```

part_dict = {'boot': options.disk_boot, 'swap': options.disk_swap, 'root': options.disk_root, 'tmp': options.disk_tmp, 'usr': options.disk_usr, 'var': options.disk_var, 'home': options.disk_home}

for key, var in part_dict.iteritems():
        if var == "GROW":
                print key, "is set to", var

```

How do I now change that variable ?

Just keep in mind, all those comes from OptionParser : 

```

parser.add_option("--home", dest="disk_home",
                help="Size of /home in MB or GROW",
                metavar="MB")

```

That is why they are all options.xxxx

Thd.

---

### Post by Arndt on 2009-04-16
> **thirddeep said:**
> Right, I have :

```

part_dict = {'boot': options.disk_boot, 'swap': options.disk_swap, 'root': options.disk_root, 'tmp': options.disk_tmp, 'usr': options.disk_usr, 'var': options.disk_var, 'home': options.disk_home}

for key, var in part_dict.iteritems():
        if var == "GROW":
                print key, "is set to", var

```

How do I now change that variable ?

Just keep in mind, all those comes from OptionParser : 

```

parser.add_option("--home", dest="disk_home",
                help="Size of /home in MB or GROW",
                metavar="MB")

```

That is why they are all options.xxxx

Thd.

Maybe something like this:
```

def test(o, a):
    if getattr(o,a,"null") == "GROW":
        setattr(o,a,"--size 1 --grow")

class options:
    disk_swap = "GROW"
    disk_boot = "fixed"

o = options()
print o.disk_swap
print o.disk_boot

print

test(o, "disk_swap")
test(o, "disk_boot")
test(o, "disk_root")
print o.disk_swap
print o.disk_boot

```

---

### Post by Tony Flury on 2009-04-16
> **thirddeep said:**
> Right, I have :

```

part_dict = {'boot': options.disk_boot, 'swap': options.disk_swap, 'root': options.disk_root, 'tmp': options.disk_tmp, 'usr': options.disk_usr, 'var': options.disk_var, 'home': options.disk_home}

for key, var in part_dict.iteritems():
        if var == "GROW":
                print key, "is set to", var

```

How do I now change that variable ?


```

for key, var in part_dict.iteritems():
        if var == "GROW":
             part_dict[key] = "--size 1 --grow"

```

Why wont that work (not tested btw) - in a dictionary, you can't change the key - but you can change the value.

---

### Post by thirddeep on 2009-04-16
Arndt's way works, it changes the actual instance value.  That way I still have to do 7 test.

As for changing the dictionary entry with "part_dict[key] = ", this does not change the instance value of options.disk_xxx.  Of course, I could then change the rest of the code to use the dictionary instead of the instance.

I have also found that I can directly iterate (although not as simple as dictionary) over the instance with :

```

for attr, value in options.__dict__.iteritems():
    print attr, value

```

I tried to use the above in conjuction with what Arndt showed me, like : 
```

for attr, value in options.__dict__.iteritems():
        if value == "GROW":
                setattr(options, value, "1 --grow")

```

But that just gives me : RuntimeError: dictionary changed size during iteration

I honestly do not know if what I am trying to do is even possible.  I just thought (perhaps wrongly) that doing 7 if statements that looks extremely similar could be done far more elegantly :_)

Thd.

---

### Post by unutbu on 2009-04-16
Change
```
 setattr(options, value, "1 --grow")
```
to
```
 setattr(options, attr, "1 --grow")
```

---

### Post by imdano on 2009-04-16
I think this will do what you want
[php]for attr, value in options.__dict__.copy().iteritems():
    if value == "GROW":
        setattr(options, attr, "1 --grow")[/php]Edit: Actually, yeah, what unutbu said.  No copy() call needed.

---

### Post by thirddeep on 2009-04-17
Thank you all very much for the help, that is working just how I wanted to now :-)

Thd.

---

