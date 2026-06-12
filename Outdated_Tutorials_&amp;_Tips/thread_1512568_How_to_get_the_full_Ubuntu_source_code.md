---
title: "How to get the full Ubuntu source code"
date: 2010-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by gzarkadas on 2010-06-18
This howto shows a method to download the entire source code of (any version of) the Ubuntu distribution, or selected entire branches, or arbitrary custom selections (if a preparatory editing step to the package lists created is inserted). 

It is also applicable to all distributions that use dpkg/apt-get as the method to manage their packages (ie Debian, etc.)

Compared to using the links from [http://cdimage.ubuntu.com/releases/](http://cdimage.ubuntu.com/releases/) to download source isos of the distribution it offers the following advantages:

[LIST]
[*]Modularity and easy customisation. You can get what you want and only that; just edit the package list(s) to your needs.
[/LIST]

[LIST]
[*]You can get packages from `universe' and `multiverse' branches, for which there is no iso image.
[*]Source packages are get automatically expanded and ubuntu patches applied. You thus get a ready for modification/compilation source tree.
[*]Responsiveness. You can start browsing sources within a few minutes.
[/LIST]
Disadvantages:

[LIST]
[*]You don't get an iso image; you 'll have to make it yourself.
[*]Since packages are auto expanded, you need more hard disk space.
[*]It needs more time to finish.
[/LIST]
The method is also friendlier to the ubuntu servers infrastructure, since the download is spread into small chunks with sleep time in between. At the moment, the tree structure is also slightly different, specifically is more flattened (for example aalib is in ./main/aalib-1.4p5 instead of ./pool/main/a/aalib).

**IMPORTANT NOTE:** Since you will be downloading *_a lot_*, pay extreme attention to not overload the ubuntu servers (be reassured that you are not alone; others will be doing it also, at the same time). This means to use large sleep times in between downloads, 20 seconds *at minimum*. There is no point to rush into downloading something that big.

[B]Step 0: Preparation
[/B]
You will need adequate disk space. The exact requirements depend on what you select for downloading but you can expect that you will need several gigabytes; plan for at least 50 GB to stay free for the next couple of weeks (see below).

Arrange to be able to leave your computer into continuous operations for up to two weeks or so. With thousands of packages (15633 packages for our example) the download process  will take approximately one to two weeks to complete.

You will need to open a terminal window (from menu `Applications|Accessories|Terminal') and type a sequence of commands into there; there is currently no GUI for achieving this operation. To ease things for those not accustomed to the command line, the commands are organised so that if all code blocks were concatenated in order they would produce the correct result. So just continue typing from where you were left and you will be fine.

Make a directory to put the source and cd to it. It is wise to use a separate directory for each distribution and for each branch of the distribution. 

_Example:_ We want the `main' and `universe' branches of the Karmic (9.10) distribution: 
```

mkdir -p ~/source/ubuntu/karmic/main
mkdir -p ~/source/ubuntu/karmic/universe
cd ~/source/ubuntu/karmic

```[B]Step 1: Acquire the list of sources for the target distribution. 
[/B]
The source lists are hosted at [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/). Each distribution is located in a separate directory and each contains four branches: `main', `universe', `multiverse' and `restricted'. Inside each branch there is a `source' subdirectory and a `Sources.gz' compressed archive inside it, which must be downloaded. 

You will have to repeat this process for each desired branch.

Get inside each subdirectory, download `Sources.gz' with `wget', unzip it to `Sources' and return back to top directory.

_Example_ -`main' and `universe' branches of the Karmic (9.10) distribution- _continued:_ 
```

cd main
wget http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz
gzip -d Sources.gz
cd ..
sleep 5  
cd universe
wget http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz
gzip -d Sources.gz
cd ..

```[B]Step 2: Extract package names from the sources list(s) into file(s) with a single package name per line
[/B]
Filter `Sources' contents with `grep' to select lines with package name and `cut' to remove the `Package: ' substring at start of each line. Save result to file `package.list'.

_Example_ -`main' and `universe' branches of the Karmic (9.10) distribution- _continued:_ 
```

cd main
cat Sources | grep 'Package: ' | cut -c10-1000 > package.list
cd ..
cd universe
cat Sources | grep 'Package: ' | cut -c10-1000 > package.list
cd ..

```[B]Step 3: Use `apt-get source ...' and the package list(s) to get the source. 
[/B]
To be able to leave the whole thing unattended and to resume relatively easy should a power failure or other event stops the process, a log file and progress file are maintained.

**IMPORTANT NOTE:** If `apt-get' permissions have been set to restrict normal users from using it, prepend `sudo' before `apt-get' inside each while loop. If a very short time out has been set for `sudo', then surround instead each of the code blocks below with `sudo -i' at start (to open a root shell) and `exit' at end (to close the root shell when done).

[I][B]Sub-step A: create the log files.
[/B][/I]
Get inside each subdirectory, use `touch' to create empty log files and return back to top directory.

_Example_ -`main' and `universe' branches of the Karmic (9.10) distribution- _continued:_ 
```

cd main
touch fetch.log
touch progress.log
cd ..
cd universe
touch fetch.log
touch progress.log
cd ..

```[I][B]Sub-step B: download sources.
[/B][/I]
**REMINDER:** *Be really nice with the Ubuntu distro servers, put a sleep 20 (at least) after each apt-get call (see note at the top of this howto).*

Get inside each subdirectory and feed all lines of the file `package.list' to the `while...do...done' loop. Inside the loop read each line into the `$pkg' shell variable and if successful (ie there is still input) call `apt-get' to fetch the source package. Duplicate the output of `apt-get' with `tee' and store it to `fetch.log' log file. Write also the name of the package to `progress.log' log file and then sleep for 20 seconds. When loop is finished, return back to top directory.

_Example_ -`main' and `universe' branches of the Karmic (9.10) distribution- _continued:_ 
```

cd main
while read pkg ; do apt-get source ${pkg} | tee -a fetch.log ; echo ${pkg} >> progress.log ; sleep 20 ; done < package.list
cd ..
cd universe
while read pkg ; do apt-get source ${pkg} | tee -a fetch.log ; echo ${pkg} >> progress.log ; sleep 20 ; done < package.list
cd ..

```**If** the process is interrupted (**and only then**), remove the last line of the progress log as well as the directory of the package in that line and the directory in the next line at package.list if they exist. Then backup the package.list and make a new one excluding all successfully downloaded packages.

_Example_ -`main' and `universe' branches of the Karmic (9.10) distribution- continued: 
```

cd <directory-where-the-process-stopped (either main or universe)>
last_line=$(cat progress.log | wc --lines)
for dir in $(cat package.list | head --lines=$((last_line + 1)) | tail --lines=2) ; do rm -R ${dir} ; done
cat progress.log | head --lines=$((last_line - 1)) > /tmp/get-source.tmp.XYZ
mv -b /tmp/get-source.tmp.XYZ progress.log
cp package.list package.list.bak
cat package.list.bak | tail --lines=+$((last_line - 1)) > package.list
unset last_line
cd ..

```Now you can go back in Step 3, Sub-step B (_ATTENTION:_ here you must not `touch' the logs; they will get erased!).

[B]Step 4: Review the logs and take care to fix possible errors.
[/B]
The steps necessary depend on the specific plans for code utilisation. As a minimum, ensure that all packages are downloaded and no errors showed up.

Get inside each subdirectory. Use `diff' to compare the package list with the progress log; if all packages where downloaded they should be identical. Then use `grep' to scan the output of `apt-get' that was duplicated to `fetch.log' for errors. Return back to top directory.

_Example_ -`main' and `universe' branches of the Karmic (9.10) distribution- _continued:_ 
```

cd main

[COLOR=Blue]# the two commands below should not produce visible output
[/COLOR]diff -U 0 progress.log package.list
grep -C 0 'dpkg-source: error:' fetch.log

cd ..
cd universe

[COLOR=Blue]# the two commands below should not produce visible output
[/COLOR]diff -U 0 progress.log package.list
grep -C 0 'dpkg-source: error:' fetch.log

cd ..

```If you have errors, then either resolve them manually, or use the package.list file and an editor to produce a subset with the packages in problem and feed it to the commands presented above in step 3.

[B]Step 5: Seat back and relax
[/B]
You are done; enjoy your source Ubuntu distribution! If you fiddle with the code, don't forget to return your changes to the community.

---

