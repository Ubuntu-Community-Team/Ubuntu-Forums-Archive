---
title: "Easy rsync scripts"
date: 2009-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Buce on 2009-08-01
If you've ever looked at the rsync manpages, you know what a horror that can be when all you want to do is transfer a handful of files over to another computer. These two scripts are designed to make that easy. The syntax for them is:

```
#Download files from another computer
get file1 file2 file3... from computer1

#Upload files to a computer
put file1 file2 file3... on computer2
```

You pick whatever you want to call computer1/computer2 in a configuration file. That's the gist of it -- heres the setup:

First, we're going to create the configuration file. I put all my personal config files in ~/.etc, and that's where the script points to, so that's what my instructions will use. If you want to put your file somewhere else, you'll have to change the 8th line of these scripts. The name I chose for the file is hosts.conf; if you want a different name, again, you'll have to change line 8 of the scripts.

Enter this from the command line:

```
mkdir ~/.etc
gedit .etc/hosts.conf
```

This will open up a new text file, where you'll put the 'profiles' you want to be able to rsync to and from with these scripts. Suppose you have a profile you want to call 'betty'. If your username on that computer is 'boop', and the IP address is 192.168.1.24, the syntax you would use for this new file would be:

```
betty    boop@192.168.1.24:
```

With this setup, any files you upload to 'betty' will wind up in your home directory. If you want to use a different directory, the syntax would be:

```
betty    boop@192.168.1.24:/path/to/upload/directory
```

You can add more computers, one per line, so long as the first word on each line is different. Note that this means you can set up different profiles for different accounts on the same computer, or different upload folders on the same account. F'rex, your hosts.conf file might wind up looking something like this:

```

betty-boop      boop@192.168.1.24:
betty-crocker   crocker@192.168.1.24:         # same computer, different user
betty-spaghetty boop@192.168.1.24:~/spaghetty # same computer and user as the first, different upload directory
betty-rubble    betty@rubble.com:             # if your computer has a domain name, you can use that too
```

Now, download the attached scripts. From the terminal, go to the directory you downloaded them to and make them executable. Then, use them with the appropriate syntax:

```
cd /path/to/scripts
chmod 700 get.sh put.sh
./get.sh /path/to/file1 /path/to/file2 from profile1
ls   # should display file1 and file2, if all went well
./put.sh file1 file2 file3 on computer2   # files will be uploaded to profile2
```

Note that, unlike with put.sh, the upload directories you choose in hosts.conf don't affect get.sh -- all files are downloaded to the current directory. /path/to/file1 refers to the path on the remote computer you're trying to access.

If you want to use the scripts like a normal program from the command line, without the './' at the beginning and the '.sh' part, you need to put them in a place where BASH will see them. I prefer ~/bin:
```
mkdir ~/bin
mv get.sh ~/bin/get
mv put.sh ~/bin/put
```

Now, close your terminal and open a new one. If invoking 'get file1 file2... from profile' and 'put file1 file2... on profile' from the command line doesn't work, you need to add ~/bin to your $PATH variable.

```
echo '[ -d ${HOME}/bin ] && export PATH="${HOME}/bin:${PATH}"' >> ~/.bashrc
```

Closing your terminal and opening a new one again should do the trick.

---

