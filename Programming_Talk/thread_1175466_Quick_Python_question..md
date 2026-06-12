---
title: "Quick Python question."
date: 2009-06-01
forum: Programming Talk
---

### Post by NFblaze on 2009-06-01
Alright, so I have Python 2.6.2 installed on my computer. I've decided to see if maybe I can start re-learning a little bit more about programming. So I have this book called 'Beginning Python From Novice to Professional'

Everything is good, seems pretty familiar still. Anyhow the question I had was that apparently you can add the crunchbang and the environmental variable path to the program that will automatically launch the script. 

I followed the book and added

 <code>#!/usr/bin/env python</code>

, but the script wont run if I try it thru my terminal. Anything Im missing something

---

### Post by CptPicard on 2009-06-01
Make it executable:

```

chmod +x your_script.py

```

---

### Post by Tibuda on 2009-06-01
You need to make the script executable. You can right-click the file in nautilus, and add the executing permissions in the file properties. Or you can do it in the terminal with
```
chmod a+x filename.py
```

---

### Post by NFblaze on 2009-06-01
I did make the file executable and still no luck. 

For some reason it wont show up as a valid file when I try to see if it'll run if I use tab completion.

I was able to recently see my /usr/bin/env and it seems like python is not defined. Tho when I use nano /usr/bin/env it seems to open a manual for ENV.

---

### Post by finer recliner on 2009-06-01
type ```
which python
```

this will tell you the path to where your python interpreter is intalled. copy that path to crunchbang line (with the #! in front of it)

example:
```
#!/path/to/python

print "hello world!"

```

---

### Post by NFblaze on 2009-06-01
> **finer recliner said:**
> type ```
which python
```

this will tell you the path to where your python interpreter is intalled. copy that path to crunchbang line (with the #! in front of it)

example:
```
#!/path/to/python

print "hello world!"

```

The script already has that in it. This is what the script says..

```

#!/usr/bin/python
name = raw_input("What is your name? ")
print "Hello, " + name + "!"
```

Really is stumping me. This is what I put in the terminal and what I recieve.
```
infiltrat3annihilat3s3iz3@Infiltrat3Annihilat3S3iz3-mobe:~$ cd Python/
infiltrat3annihilat3s3iz3@Infiltrat3Annihilat3S3iz3-mobe:~/Python$ yourname.py
bash: yourname.py: command not found
infiltrat3annihilat3s3iz3@Infiltrat3Annihilat3S3iz3-mobe:~/Python$ ls -l
total 8
-rwxr-xr-x 1 infiltrat3annihilat3s3iz3 infiltrat3annihilat3s3iz3 87 2009-06-01 14:51 yourname.py
-rw-r--r-- 1 infiltrat3annihilat3s3iz3 infiltrat3annihilat3s3iz3 87 2009-06-01 14:44 yourname.py~
infiltrat3annihilat3s3iz3@Infiltrat3Annihilat3S3iz3-mobe:~/Python$ 

```

---

### Post by Tibuda on 2009-06-01
to run a script from the current folder you have to prefix it with ./
```
infiltrat3annihilat3s3iz3@Infiltrat3Annihilat3S3iz3-mobe:~$ cd Python/
infiltrat3annihilat3s3iz3@Infiltrat3Annihilat3S3iz3-mobe:~/Python$ ./yourname.py

```

---

### Post by meastp on 2009-06-01
> **danielrmt said:**
> to run a script from the current folder you have to prefix it with ./
```
infiltrat3annihilat3s3iz3@Infiltrat3Annihilat3S3iz3-mobe:~$ cd Python/
infiltrat3annihilat3s3iz3@Infiltrat3Annihilat3S3iz3-mobe:~/Python$ ./yourname.py

```

alternatively, just run it with ```
:~/Python$ python yourname.py
```

---

### Post by NFblaze on 2009-06-01
> **danielrmt said:**
> to run a script from the current folder you have to prefix it with ./
```
infiltrat3annihilat3s3iz3@Infiltrat3Annihilat3S3iz3-mobe:~$ cd Python/
infiltrat3annihilat3s3iz3@Infiltrat3Annihilat3S3iz3-mobe:~/Python$ ./yourname.py

```

Success!

That did the trick.W00t W00t. Awesome. Thanks.

---

