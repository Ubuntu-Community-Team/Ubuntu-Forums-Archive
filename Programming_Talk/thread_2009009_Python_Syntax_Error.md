---
title: "Python Syntax Error"
date: 2012-06-23
forum: Programming Talk
---

### Post by Dubslow on 2012-06-23
Gah...

This is probably one of things with a missing parenthesis or some sort of whitespace error but... I can't find it.

I'm using gedit with tabs set to 5 spaces, and using actual spaces (instead of \t).

```
#! /usr/bin/python3

from urllib import request, parse, error
from time import strftime
import re, sys
FILE = '/home/bill/wobsite/random/AllSeq.html'
timefmt = '%A %Y/%m/%d @ %H:%M'
print('\n'+strftime(timefmt))
timefmt += ' UTC'

per_hour = 100

composite = re.compile(r'=.+<font color="#002099">[0-9.]+</font></a><sub>&lt;(?P<C>[0-9]+)')
smallfact = re.compile(r'(?:<font color="#000000">)([0-9^]+)(?:</font></a>)(?!<sub>)')
largefact = re.compile(r'(?:<font color="#000000">[0-9^.]+</font></a><sub>&lt;)([0-9]+)')
stuff = re.compile('<td bgcolor="#BBBBBB">n</td>\n<td bgcolor="#BBBBBB">Digits</td>\n<td bgcolor="#BBBBBB">Number</td>\n</tr><tr><td bgcolor="#DDDDDD">Unchecked</td>\n<td bgcolor="#DDDDDD">(?P<index>[0-9]+)</td>\n<td bgcolor="#DDDDDD">(?P<size>[0-9]+) <a href=' )
oldpage = re.compile('<tr> <td>(?P<seq>[0-9]+?)</td> <td>(?P<sz>[0-9]+?)</td> <td>(?P<ind>[0-9]+?)</td> <td>(?P<facts>.*?)</td> <td>(?P<time>.*?)</td>')

seqs = [854628, 276, 966] # Will eventually be ~9000 entries once I prove the script works
data = []
this = seqs[start : per_hour+start]

with open(sys.argv[0]+'.conf', 'r') as conf:
     start = int(conf.readline())


               

html = """ A rather large 
     multiline chunk of 
html here"""

class Sequence:
     def __init__(self, seq=0, size=0, index=0, factors=None, time=None):
          self.seq = seq
          self.index = index
          self.size = size
          self.time = time
          self.factors = factors # A concatenated string of the factors of the latest line (only used in reading old data)
               
with open(FILE, 'r') as asdf:
     olddat = oldpage.findall(asdf.read())
     if olddat:
          for dat in olddat:
               if int(dat.group('seq')) not in this:
                    data.append(Sequence(int(dat.group('seq')), int(dat.group('sz')), int(dat.group('ind')), factors=dat.group('facts'), time=dat.group('time') )

for seq in this:
     req = request.Request('http://<valid url>'+str(seq),
         headers = {'User-Agent': '<description>'} )
     try:
          page = request.urlopen(req).read().decode('utf-8')
     except error.HTTPError as e:
         print('HTTPError:', e)
     else:
          if 'Not all factors known' in page:
               info = stuff.search(page)
               comps = composite.findall(page)
               smalls = smallfact.findall(page)
               bigs = largefact.findall(page)
               if info:
                    ali = Sequence(seq, int(info.group('size')), int(info.group('index')))
                    factors = ''
                    try:
                         factors += smalls[0]
                         smalls = smalls[1:]
                         for small in smalls:
                              factors += " * "+small
                    except AttributeError: print('Seq:', seq, "no smalls match")
                    if bigs:
                         for big in bigs:
                              factors += " * P"+big
                    else: print('Seq:', seq, "no bigs match")
                    if comps:
                         for comp in comps:
                              factors += " * C"+comp
                    else: print('Seq:', seq, "no comps match")
                    ali.factors = factors
                    data.append(ali)
               else: print('Seq:', seq, "no info match. Page:"); print(page)
          else: print('Seq:', seq, 'all factors known or something.')

dato = sorted(data, key=lambda ali: ali.size)

with open(FILE, "w") as f:
     f.write(html)
     for i in range(len(dato)):
          out =  """          <tr> <td>{:d}</td> <td>{:d}</td> <td>{:d}</td> <td>{:s}</td> <td>{:s}</td> </tr>""".format(
                                dato[i].seq, dato[i].size, dato[i].index, dato[i].factors, strftime(timefmt, gmtime()) )
          f.write(out+"\n")
     f.write("""     </tbody>\n     </table>\n</body>\n</html>\n""")

with open(sys.argv[0]+'.conf', 'w') as conf:
     start = (start + per_hour) % len(seqs)
     conf.write(str(start)+'\n')
```
It's meant to be run hourly from a crontab, if/when I get it to work. It gets/parses some data, outputting it in html format to an html file, with errors to stdout to be redirected in the crontab to a log file.

No matter absolutely anything I do, all I ever get is this (or something like it):
```
>>> import allseq
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "allseq.py", line 74
    for seq in this:
                   ^
SyntaxError: invalid syntax
>>> ^D
bill@Gravemind:~/bin/py&#8752;&#8706; allseq.py 
  File "/home/bill/bin/py/allseq.py", line 74
    for seq in this:
                   ^
SyntaxError: invalid syntax
bill@Gravemind:~/bin/py&#8752;&#8706;
```

---

### Post by Simian Man on 2012-06-23
You have mismathced parenthesis on this line:

data.append(Sequence(int(dat.group('seq')), int(dat.group('sz')), int(dat.group('ind')), factors=dat.group('facts'), time=dat.group('time') )

Presumably you should add a ) at the end.  Though that line should really be split up to avoid this kind of problem.

---

### Post by Dubslow on 2012-06-23
I thought so! 

But then, I had also thought I had checked all the parentheses pairs (gedit has a nice paren-highlight tool). I guess not! :p

Thanks! [/stupid]

---

