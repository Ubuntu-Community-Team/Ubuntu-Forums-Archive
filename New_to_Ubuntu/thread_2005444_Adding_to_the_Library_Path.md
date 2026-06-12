---
title: "Adding to the Library Path"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by koenigcochran on 2012-06-17
Hi,

I've now read way too many threads and articles on how to add directories to the library path. Many of them disagree and none have been helpful. 

I'm using the most recent 64-bit ubuntu release. 

I would like to permanently add ```
/home/jacob/Dakota/bin
``` to the library path. Any help would be much appreciated. Thanks!

---

### Post by lkraemer on 2012-06-18
The first step is to Always include your Current Distro, your Version, and 32 Bit or 64 Bit.

The second step you need to do is to find the "SHELL" and "env" you are using.

1. env -- Display the current environment, find what Shell is being used with the following command.....
```

    env | grep SHELL=

```
You can also type:
```

    env > envorig.txt

```
to create a file of the results to attach. In fact go ahead and do this
and attach the file so we can view it. Later you can do a comparison for future reference.

2. locate .*rc -- Find the current logged in user's home shell Configuration file (*rc)... use:
```

locate .*rc

```
REF:
[http://en.wikipedia.org/wiki/Unix_shell](http://en.wikipedia.org/wiki/Unix_shell)
Bourne shell (sh)
Almquist shell (ash)
Bourne-Again shell (bash)
Debian Almquist shell (dash)
Korn shell (ksh)
Z shell (zsh)
C shell (csh)
TENEX C shell (tcsh)
other shells..............

There may be a .bash_profile file in /home/loginuser along with .bashrc. You can put configurations in either file,
and you can create either if it doesn&#8217;t exist. But, why two different files? What is the difference? 

According to the bash man page, .bash_profile is executed for login
shells, while .bashrc is executed for interactive non-login shells.

If .bash_profile exists in /home/user with the following information already inserted:
```

	PATH=$PATH:$HOME/bin
	export PATH

```
just append your path modifications here instead of the .bashrc file. (ie. CentOS 6)

You need to list the *rc file to verify the contents and set the PATHS. I'm ASSUMING a Bash shell......Your may be different!

3. cat .bashrc -- List the configuration file, then append the proper search paths for the users shell with edit.
> 
export LD_LIBRARY_PATH=????????????????????????????????
export LIBRARY_PATH=???????????????????????????????????
export C_INCLUDE_PATH=?????????????????????????????????
export CPATH=??????????????????????????????????????????

Mine happens to now be:
> 
export LD_LIBRARY_PATH=/usr/lib:/usr/local/lib
export LIBRARY_PATH=/usr/lib:/usr/local/lib
export C_INCLUDE_PATH=.:/usr/include:/usr/local/include
export CPATH=.:/usr/include:/usr/local/include

But your may vary accordingly. You won't be able to cut & paste mine,
unless your system is built exactly like mine. It's up to you to locate
exactly where all the libs and includes are located. That is what all the
previous commands should have helped you do. Just because you have
/usr/lib & /usr/local/lib included....**doesn't mean your needed lib is in that path.**

That is where your detective work comes to play. SEARCH and use grep to locate the libs.

Once you have the env set either reboot or reset the env. Once again, your system command for this can/may be different.

4. source .bashrc -- Reset the environment to what we need for Compiles, assuming the SHELL is bash. This may not be available on your system.....

REF:
[http://linux.about.com/library/cmd/blcmdl1_ulimit.htm](http://linux.about.com/library/cmd/blcmdl1_ulimit.htm)
> 
source filename [arguments]
    Read and execute commands from filename in the current shell environment and return the exit status of the last command executed from filename. If filename does not contain a slash, file names in PATH are used to find the directory containing filename. The file searched for in PATH need not be executable. When bash is not in posix mode, the current directory is searched if no file is found in PATH. If the sourcepath option to the shopt builtin command is turned off, the PATH is not searched. If any arguments are supplied, they become the positional parameters when filename is executed. Otherwise the positional parameters are unchanged. The return status is the status of the last command exited within the script (0 if no commands are executed), and false if filename is not found or cannot be read. 



VERIFY the env is correct:

5. env -- Display the new environment to verify the paths.............PARTIAL DISPLAY of SPECIFIC's I NEEDED...
> 
LIBRARY_PATH=/usr/lib:/usr/local/lib
LD_LIBRARY_PATH=/usr/lib:/usr/local/lib
CPATH=.:/usr/include:/usr/local/include
C_INCLUDE_PATH=.:/usr/include:/usr/local/include

Since your env is now set as you need, save env contents to another file named envnew.txt. Later, you can use
Meld to compare the two files.


lk

---

### Post by _0R10N on 2012-06-18
For me the best (and quickest way) is to append the desired directory to the PATH variable located on your .bashrc file.
```
echo "PATH=$PATH:/home/jacob/Dakota/bin" >> .bashrc
```

---

