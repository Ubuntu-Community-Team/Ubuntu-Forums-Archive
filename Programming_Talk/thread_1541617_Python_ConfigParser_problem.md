---
title: "Python ConfigParser problem"
date: 2010-07-29
forum: Programming Talk
---

### Post by satman-ga on 2010-07-29
Environment:
Ubuntu 8.04
Python 2.5.2

I am trying to use the ConfigParser module to read from an INI file. 
```
Config = ConfigParser.ConfigParser()
Config.read('/home/satman/.program/program.ini')
ip = Config.get('http','ip')
port = Config.get('http','port')

```
I've had success with most files, but I've recently run into a problem with a particular INI. The first line of the file contains version info that is not contained within a section header. 
```
__version__ = 22
[http]
port = 8085
ip = localhost
```
This results in the script exiting with the following exception:
```
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /home/satman/.program/.program.ini, line: 1
'__version__ = 22'
```

Short of deleting that line from the file, is there a way to work around this or another module that is useful for parsing INI files that is more tolerant of situations like this?

---

### Post by DaithiF on 2010-07-29
Hi, you could open the file, read the first line, then tell config parser to read the rest.

```
fh = open('/home/satman/.program/.program.ini', 'rb')
fh.readline()    # discard first line
config.readfp(fh)

```

---

### Post by satman-ga on 2010-07-29
Thanks. That avoided the missing section header error, but now I get an error stating that there is no section named http. Here is the code as I implemented it.
```
Config = ConfigParser.ConfigParser()
inif = open('/home/satman/.program/program.ini','rb')
inif.readline()
Config.read(inif)
ip = Config.get('http','ip')
port = Config.get('http','port')
```

---

### Post by DaithiF on 2010-07-30
Hi,
You didn't quite do what I suggested.
```
Config.read(inif)

```
can you see a difference between this and my suggestion?

---

### Post by satman-ga on 2010-07-30
```
Config.read(inif)
```
changed to 
```
Config.readfp(inif)
```
Thanks so much. It worked like a charm when I followed directions.

---

