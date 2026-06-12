---
title: "Anonymize Data"
date: 2011-08-01
forum: Programming Talk
---

### Post by ShareBuntu on 2011-08-01
Hello,

Does anyone know of a script or application to anonymize network data (in .CSV format)? I've got some new network data I've collected and I want to make it available in the public domain. I've got CSV files that look like this:

ACTORA,ACTORB
ACTORA,ACTORC
ACTORB,ACTORD,ACTORF,ACTORG,ACTORH
ACTORC,ACTORD,ACTORG,ACTORI,ACTORJ
ACTORC,ACTORE

I'm trying to convert ACTORA to 1 and ACTORB to 2, etc. I.e., I want it to look like this:

1,2
1,3
2,4,5,6,7
3,4,6,8,9
3,10

Does anyone know how to do this? Have a look at the data sets at [http://snap.stanford.edu/data/index.html](http://snap.stanford.edu/data/index.html). That format would be perfect. I'd really appreciate your help on this, as I want to make the data available to the community. :D

Thank you kindly!

---

### Post by Bachstelze on 2011-08-01
Just use sed

```
sed 's/ACTORA/1/g; s/ACTORB/2/g' input.txt
```

---

### Post by karlson on 2011-08-01
> **ShareBuntu said:**
> Hello,

Does anyone know of a script or application to anonymize network data (in .CSV format)? I've got some new network data I've collected and I want to make it available in the public domain. I've got CSV files that look like this:

ACTORA,ACTORB
ACTORA,ACTORC
ACTORB,ACTORD,ACTORF,ACTORG,ACTORH
ACTORC,ACTORD,ACTORG,ACTORI,ACTORJ
ACTORC,ACTORE

I'm trying to convert ACTORA to 1 and ACTORB to 2, etc. I.e., I want it to look like this:

1,2
1,3
2,4,5,6,7
3,4,6,8,9
3,10

Does anyone know how to do this? Have a look at the data sets at [http://snap.stanford.edu/data/index.html](http://snap.stanford.edu/data/index.html). That format would be perfect. I'd really appreciate your help on this, as I want to make the data available to the community. :D

Thank you kindly!

Sounds like a homework problem.

It's a simple hash substitution.

---

### Post by karlson on 2011-08-01
> **Bachstelze said:**
> Just use sed

```
sed 's/ACTORA/1/g; s/ACTORB/2/g' input.txt
```

I think in the problem is that the keys are not limited and need to be counted in order of appearance.

---

### Post by ShareBuntu on 2011-08-01
Thank you for the response. This isn't a homework problem. I've collected a lot of network data for a thesis ([http://en.wikipedia.org/wiki/Social_network#Social_network_analysis](http://en.wikipedia.org/wiki/Social_network#Social_network_analysis)). The problem that I have is that I can't release it into the public domain for other researcher to analyse unless I can anonymize the data. Someone suggested a Python script, but unfortunately I have no idea how to write it. Since the Ubuntu community was very helpful in the past when I switched over, I thought I would consult its experts on this.

---

### Post by AureiAnimus on 2011-08-01
This is python:
```
#!/usr/bin/env python
import sys

hashes = {}
count = 1
with open(sys.argv[1]) as f1:
    for line in f1:
        actors = line.strip("\n").split(',')
        hashActors = []
        for actor in actors:
            try:
                hashActors.append(hashes[actor])
            except KeyError:
                hashes[actor] = str(count)
                hashActors.append(str(count))
                count += 1
        print ",".join(hashActors)
```
Usage: save as, say: anonimizer.py, put the csv in the same directory and run:

python anonimizer.py old.csv > new.csv

Provided AS IS, but feel free to ask if you run into trouble ;)

---

### Post by ShareBuntu on 2011-08-01
> **AureiAnimus said:**
> This is python:
```
#!/usr/bin/env python
import sys

hashes = {}
count = 1
with open(sys.argv[1]) as f1:
    for line in f1:
        actors = line.strip("\n").split(',')
        hashActors = []
        for actor in actors:
            try:
                hashActors.append(hashes[actor])
            except KeyError:
                hashes[actor] = str(count)
                hashActors.append(str(count))
                count += 1
        print ",".join(hashActors)
```
Usage: save as, say: anonimizer.py, put the csv in the same directory and run:

python anonimizer.py old.csv > new.csv

Provided AS IS, but feel free to ask if you run into trouble ;)
This code just saved my life. I want to thank you in the acknowledgment section of the thesis. How may I refer to you (if you don't mind, of course)? :)

---

