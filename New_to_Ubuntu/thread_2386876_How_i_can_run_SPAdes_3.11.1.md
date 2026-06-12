---
title: "How i can run SPAdes 3.11.1"
date: 2018-03-11
forum: New to Ubuntu
---

### Post by cdv22 on 2018-03-11
Hi
excuse my english, I am a new user in ubuntu for which, I want to  apologize also for this question study question that I am doing.
I want to run SPAdes 3.11.1 in Ubuntu 14.04, but I don’t know how to run  the package, if someone could explain step by step how I can run the  package, I will be very grateful.
Additionally I have installed the packages phyton and java
 Thanks for reading this.

---

### Post by tinylagarto on 2018-03-11
Usually people will open the software center, Gnome Software, and install it from there.

But you can also use the command line and typing this into a terminal:

```
 sudo apt install spades
```

and it will install the package spades. 

Did I understand your question correctly?

---

### Post by monkeybrain20122 on 2018-03-11
> **ivanovnegro2 said:**
> Usually people will open the software center, Gnome Software, and install it from there.

But you can also use the command line and typing this into a terminal:

```
 sudo apt install spades
```

and it will install the package spades. 

Did I understand your question correctly?

There is no package in the 14.04 repository called spades [http://bioinf.spbau.ru/spades](http://bioinf.spbau.ru/spades) It is in artful and bionic, the site also provides a binary, just download, extract and run.

---

### Post by Impavidus on 2018-03-11
Spades is only available from the repositories from Ubuntu 17.10 onward. Ubuntu 17.10 has version 3.10.1, Ubuntu 18.04 (which hasn't been released yet and it's not recommended to use it unless you want to test) has 3.11.1 in the repositories. I don't think that installing it on such an old release as 14.04 (it's supported, but old anyway) is the best solution to your problem.

[https://packages.ubuntu.com/artful/spades](https://packages.ubuntu.com/artful/spades)

---

### Post by monkeybrain20122 on 2018-03-11
I don't think you are asking how to install it since it doesn't need to install, as to how to use it its manual is quite detail I think
[http://spades.bioinf.spbau.ru/release3.11.1/manual.html](http://spades.bioinf.spbau.ru/release3.11.1/manual.html)

---

### Post by cdv22 on 2018-03-11
Hi
 thank you for answering me, I followed the instructions on its website (with any of the versions of the package), and it installed a folder with the same name of the package. Inside this folder there are two, one with the name "bin" and another "share" but I don't know how to start the package. 
pd: I have used the program, but from a server, that's why I ask for the help of some of you. 
thanks

---

### Post by again? on 2018-03-11
Spades comes with some testing data.
After extracting the spades tar.gz download, you can test with
```
/*[COLOR="#696969"]YourPathTo[/COLOR]*/SPAdes-3.11.1-Linux/bin/spades.py --test
```
as shown in monkeybrain20122's link. [Verifying your installation]("http://spades.bioinf.spbau.ru/release3.11.1/manual.html#sec2.4")

---

### Post by cdv22 on 2018-03-11
Hi, I couldn't, it answers me 
"command not found: spades.py"
but in the "bin" folder with the command *ls* the script appears: 

ls[ 5:34PM]
bwa-spades
dipspades.py 
metaspades.py 
scaffold_correction
spades.py
corrector hammer plasmidspades.py
 spades truspades.py
dipspades ionhammer rnaspades.py 
spades_init.py

---

### Post by again? on 2018-03-11
I downloaded SPAdes-3.11.1-Linux.tar.gz and the test ran ok.
```
[COLOR="#006400"]**glen@Xubarty:~$[/COLOR] cd ~/Downloads**
[COLOR="#006400"]**glen@Xubarty:~/Downloads$[/COLOR] wget [http://cab.spbu.ru/files/release3.11.1/SPAdes-3.11.1-Linux.tar.gz](http://cab.spbu.ru/files/release3.11.1/SPAdes-3.11.1-Linux.tar.gz)**
--2018-03-12 06:44:57--  [http://cab.spbu.ru/files/release3.11.1/SPAdes-3.11.1-Linux.tar.gz](http://cab.spbu.ru/files/release3.11.1/SPAdes-3.11.1-Linux.tar.gz)
Resolving cab.spbu.ru (cab.spbu.ru)... 185.44.15.200
Connecting to cab.spbu.ru (cab.spbu.ru)|185.44.15.200|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10537700 (10M) [application/octet-stream]
Saving to: 'SPAdes-3.11.1-Linux.tar.gz’

SPAdes-3.11.1-Linux.tar.gz      100%[=====================================================>]  10.05M   631KB/s    in 23s     

2018-03-12 06:45:21 (443 KB/s) - 'SPAdes-3.11.1-Linux.tar.gz’ saved [10537700/10537700]

[COLOR="#006400"]**glen@Xubarty:~/Downloads$[/COLOR] tar -xzf SPAdes-3.11.1-Linux.tar.gz**
[COLOR="#006400"]**glen@Xubarty:~/Downloads$[/COLOR] cd SPAdes-3.11.1-Linux/bin**
[COLOR="#006400"]**glen@Xubarty:~/Downloads/SPAdes-3.11.1-Linux/bin$[/COLOR] ./spades.py --test**
```

I can also run with...
```
~/Downloads/SPAdes-3.11.1-Linux/bin/spades.py --test
```
ie
```
[COLOR="#006400"]**glen@Xubarty:~$[/COLOR] ~/Downloads/SPAdes-3.11.1-Linux/bin/spades.py --test**
Command line: /home/glen/Downloads/SPAdes-3.11.1-Linux/bin/spades.py	--test	

System information:
  SPAdes version: 3.11.1
  Python version: 2.7.14
  OS: Linux-4.13.0-36-generic-x86_64-with-Ubuntu-17.10-artful

Output dir: /home/glen/spades_test
Mode: read error correction and assembling
Debug mode is turned OFF

[COLOR="#696969"]<----------------------------------SNIP----------------------------------->[/COLOR]

===== Assembling finished. Used k-mer sizes: 21, 33, 55 

 * Corrected reads are in /home/glen/spades_test/corrected/
 * Assembled contigs are in /home/glen/spades_test/contigs.fasta
 * Assembled scaffolds are in /home/glen/spades_test/scaffolds.fasta
 * Assembly graph is in /home/glen/spades_test/assembly_graph.fastg
 * Assembly graph in GFA format is in /home/glen/spades_test/assembly_graph_with_scaffolds.gfa
 * Paths in the assembly graph corresponding to the contigs are in /home/glen/spades_test/contigs.paths
 * Paths in the assembly graph corresponding to the scaffolds are in /home/glen/spades_test/scaffolds.paths

======= SPAdes pipeline finished.

========= TEST PASSED CORRECTLY.

SPAdes log can be found here: /home/glen/spades_test/spades.log

Thank you for using SPAdes!

```


If an executable is not in your $PATH then you need to run it with an absolute path even if you are in the directory that contains the executable.
"./"  symbolizes the current directory.
So when in terminal, if you have already changed directory to where the executable is you can just precede the executable with "./" 
which in effect is providing the absolute path.
```
cd ~/Downloads/SPAdes-3.11.1-Linux/bin
./spades.py --test
```

Which is the same as running...
```
~/Downloads/SPAdes-3.11.1-Linux/bin/spades.py --test
```

P.S. (If you don't know)
The tilde ~ expands to your home directory.
Try
```
echo ~
echo $HOME
```

---

### Post by cdv22 on 2018-03-17
thanks

---

