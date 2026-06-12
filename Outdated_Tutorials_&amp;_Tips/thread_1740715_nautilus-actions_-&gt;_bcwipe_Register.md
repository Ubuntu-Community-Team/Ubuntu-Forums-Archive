---
title: "nautilus-actions -&gt; bcwipe Register"
date: 2011-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by oklokl on 2011-04-27
[http://www.jetico.com/wiping-bcwipe/](http://www.jetico.com/wiping-bcwipe/)



BCWipe-1.9-8.tar.gz

./configure
make
make install


sudo apt-get install nautilus-actions
Rebooting system-->





nautilus-actions-config-tool
(&#49884;&#49828;&#53596;>&#44592;&#48376;&#49444;&#51221;>&#45432;&#54008;&#47084;&#49828; &#46041;&#51089; &#49444;&#51221;)



&#46321;&#47197;

/usr/local/bin/bcwipe -r -p -I 
%M


&#46041;&#51109; name [I]bcwipe(user XXX) Context Lable
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190157&stc=1&d=1303914008[/IMG]

[/I]Right click the file, click
 Bcwipe action file
 It is similar to BleachBit


sudo  bcwipe -F -mz -v /media/test  (1&#54924;&#47564; &#54616;&#47140;&#47732; &#51060;&#47111;&#44172; &#54616;&#47732; &#46104;&#45348;&#50836;..)
(Wipe free space on specified filesystem.)
[URL="http://www.jetico.com/linux/bcwipe-help/wu_using.htm#file"]
[/URL]
[http://www.jetico.com/linux/bcwipe-help/wu_using.htm#file](http://www.jetico.com/linux/bcwipe-help/wu_using.htm#file)t
 &#49444;&#47749;&#49436;
 
bcwipe [-bBdfFhiIprsvVw] [-m mode] [-n delay] [-l[log_file]] [-t threads] FILE1 [ FILE2]
Wiping mode
-mb     German BCI/VSITR 7-pass wiping.
-md     U.S. DoD 5200.22M 7-pass extended character rotation wiping.
-m n     U.S. DoD 5200.22M-style n-pass extended character rotation wiping.
-me     U.S. DoE 3-pass wiping.
-mffilename     
Read wiping scheme from filename file. Scheme file format:
pass_number. {random|complementary|hex[,hex[,hex[,hex]]] [,verify]}
random - random pass
complementary - a pass complementary to previous one
hex - two-digit hex number representing static pattern
verify - verify the pass
Example:
1. random
2. complementary, verify
3. AA,A5,55
-mg     35-pass Peter Gutmann's scheme (default)
-ms     7-pass Bruce Schneier's scheme
-mt     1-pass test mode. The 4-byte head of each 512-byte block is stamped by sequential block number.
-mz     1-pass filling by zeroes
-p     Use random pattern for random passes. Much faster (especially on slow CPU) but less secure.
-s     Use ISAAC random number generator by Bob Jenkins. Default is SHA-1 (Secure Hash Algorithm).
-w     Skip data verification (wiping only).
Starting with BCWipe 1.7 all built-in wiping modes include data verification after the last wiping pass. Use -w option to disable it.
Wiping options
-n delay     Wait delay seconds between wiping passes. Modern enterprise level storage systems (NAS, disk arrays etc.) employ powerful caches. To avoid undesirable caching effects BCWipe allows you to insert adjustable delay between wiping passes. Please note that when wiping with delay between passes disk space is freed after the last pass
-b     Wipe contents of block device(s).
-B     Disable direct IO when wiping contents of block device(s).
-d     Do not delete file(s) after wiping.
-f     Force wipe files with no write permissions. Also suppress interactive mode (-i switch).
-F     Wipe free space on specified filesystem.
-I     Do not prompt whether to wipe each file.
-i     Prompt whether to wipe each file (default).
-r     Remove with wiping the contents of subdirectories recursively. (&#54616;&#50948; &#46356;&#47113;&#53552;&#47532; &#44620;&#51648; &#49325;&#51228;)
-S     Wipe files slack. File slack is the disk space from the end of a file till the end of the last cluster used by that file. Cluster is minimal portion of disk space used by file system.
-t threads     Use threads threads to wipe block devices. Useful for wiping devices with multiple drives. (&#50668;&#47084;&#44060; &#54616;&#46300; &#49325;&#51228;)
Informational options
-l [logfile]     Log program actions to logfile file. Log to console if logfile is omitted.
-v     Run in verbose mode.
-h     Display help screen and exit
-V     Display BCWipe version information and exit

---

