---
title: "Compile perl script?"
date: 2007-05-31
forum: Programming Talk
---

### Post by Eric the Red on 2007-05-31
I'm wondering how I would go about compiling a perl script?? what do I need to 'apt-get install'?? I have a perl script located at '/home/matt/Desktop/test.txt' so I tried:

 pp -o test.txt benchmark.pl

And the command pp isn't found. Any ideas?

---

### Post by trak87 on 2007-05-31
Perl is an interpreted language and doesn't compile. You just run the script. 

However, there are often programs that will compile interpreted language scripts to machine code. Is that what you are looking for?

Try perl ./benchmark.pl

---

### Post by nitro_n2o on 2007-05-31
ohh yeah, just as trak said its an interpreted language, you don't have to compile, isn't this great ;).. 
Perl comes with Ubuntu by default you just type: 
perl filename.pl

or but this in the first line of the file 
#!/usr/bin/perl -w 
and from the shell: 
sudo chmod u+x filename.pl 
which makes it an executable so you can run it 
./filename.pl

---

### Post by tr333 on 2007-06-02
All Perl scripts should have a .pl extension, not a .txt extension.  You should rename your test.txt file to benchmark.pl and set the execute permissions with "chmod +x benchmark.pl".  You should then be able to just run the perl script.

```

ubuntu@ubuntu~$ mv test.txt benchmark.pl
ubuntu@ubuntu~$ chmod +x benchmark.pl
ubuntu@ubuntu~$ ./benchmark.pl

```

The "pp" command that the original poster referred to is the Perl Packer, which is basically a compiler for Perl.  pp will by default create a file called a.out on linux/mac and a.exe on Windows.

To get "pp", you need to install the "PAR::Packer" module, and this requires a C compiler.  If you don't yet have gcc installed you can install it with the "build-essential" package from synaptic.

More info on pp can be found at the [PAR]("http://par.perl.org/") website.

As the other posters said previously, a compiler is not necessary to run/use Perl scripts as Perl is an interpreted language.

---

