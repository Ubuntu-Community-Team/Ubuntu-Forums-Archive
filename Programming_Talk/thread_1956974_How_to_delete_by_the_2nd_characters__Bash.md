---
title: "How to delete by the 2nd characters  Bash ?"
date: 2012-04-11
forum: Programming Talk
---

### Post by josephmills on 2012-04-11
Hello there i am writing a script and in this script there is a 

The base file that I am using looks like this 

```
	<!-- message -->
		<div class="vbclean_msgtext" id="post_message_1156896"><b>The most recent version may be found at <a href="https://wiki.ubuntu.com/EncryptedFilesystemHowto4" target="_blank">https://wiki.ubuntu.com/EncryptedFilesystemHowto4</a></b></div>
		<!-- / message -->
		<!-- message -->
		<div class="vbclean_msgtext" id="post_message_1157590">Very useful howto, I will be testing this when I move my lifebook from breezy to dapper. Thank you very much.</div>
		<!-- / message -->
		<!-- message -->
		<div class="vbclean_msgtext" id="post_message_1157720">Great &quot;howto&quot;, thanks.</div>
		<!-- / message -->
		<!-- message -->
		<div class="vbclean_msgtext" id="post_message_1166059">Ok, here we go! Used the one in the wiki.<br />
<br />
Instead of<br />
<div style="margin:20px; margin-top:5px; ">
	<div class="smallfont" style="margin-bottom:2px">Quote:</div>
	<table cellpadding="6" cellspacing="0" border="0" width="100%">
	<tr>
		<td class="ubuntu_quotebackground">
			
				cp -avx / /mnt/target
			
		</td>
	</tr>
	</table>
</div>had to use<br />
<div style="margin:20px; margin-top:5px">
	<div class="smallfont" style="margin-bottom:2px">Code:</div>
	<pre class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 50px;
		text-align: left;
		overflow: auto">sudo cp -avx / /mnt/target
sudo chown $(whoami):$(whoami) /mnt/target/home/$(whoami)</pre>
</div>and instead of <br />
<div style="margin:20px; margin-top:5px; ">
	<div class="smallfont" style="margin-bottom:2px">Quote:</div>
	<table cellpadding="6" cellspacing="0" border="0" width="100%">
	<tr>
		<td class="ubuntu_quotebackground">
			
				title           Cryptotest<br />
root            (hd0,0)<br />
kernel          /boot/vmlinuz-&lt;your kernel version here&gt; root=/dev/mapper/cryptoroot ro<br />
initrd          /boot/initrd.img-&lt;your kernel version here&gt;<br />
savedefault<br />
boot
			
		</td>
	</tr>
	</table>
</div>had to use<br />
<div style="margin:20px; margin-top:5px">
	<div class="smallfont" style="margin-bottom:2px">Code:</div>
	<pre class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 114px;
		text-align: left;
		overflow: auto">title           Cryptotest
root            (hd0,0)
kernel          /vmlinuz-&lt;your kernel version here&gt; root=/dev/mapper/cryptoroot ro
initrd          /initrd.img-&lt;your kernel version here&gt;
savedefault
boot</pre>
</div>otherwise the result was error 15 - file not found.</div>
		<!-- / message -->
		<!-- message -->
		<div class="vbclean_msgtext" id="post_message_1168131">Thanks, kaamos. I have already included your corrections in wiki.</div>
		<!-- / message -->
		<!-- message -->
		<div class="vbclean_msgtext" id="post_message_1200459">Hi, I've tried this out and have a few points.<br />
<br />
<b>1)</b> There is no mention of one having to have a separate boot-partition. <br />
I suppose it stands to reason that this would have to be the case in order for the unencrypted kernel to be read, but I think this issue should be addressed for two reasons:<br />
<b>1.1</b> Software security.<br />
With the requirement of a separate, readable boot-partition, a malicious party could install a modified kernel. <br />
<b>1.2</b> Multi-boot.<br />
With one boot-partition, one swap-partition, and one linux-partition, having windows installed as well (which to my knowledge requires a primary-partition), one runs out of partitions. <br />
Four primary partitions are allowed, <i>or</i> three primary partitions and one extended.<br />
This should be clarified initially. <br />
<br />
<b>2)</b> Other keyboard-layouts than US-ENG.<br />
Some people use different layouts than US English / QWERTY; hence with the requirement of having to type the keyphrase in US English, there may be an issue.<br />
At least this should be pointed out, at best a short explanation of how to either recompile the kernel or load a different keyboard-driver should be added.<br />
<br />
Apart from this, it is a short and functional guide. Though not complete.</div>
		<!-- / message -->
		<!-- message -->
		<div class="vbclean_msgtext" id="post_message_1202504">Information in the first post of this thread is outdated.<br />
<br />
- Additions have been made to mkinitramfs scripts to load keymap at boot time (thanks to Luc Maisonobe).<br />
- Some typos have been corrected.<br />
<br />
Once again. The most up to date version is in wiki, not here.<br />
<br />
<a href="https://wiki.ubuntu.com/EncryptedFilesystemHowto4" target="_blank">https://wiki.ubuntu.com/EncryptedFilesystemHowto4</a></div>
		<!-- / message -->
		<!-- message -->
		<div class="vbclean_msgtext" id="post_message_1208536">There is no part where you fill the disk with random data like in other HOWTOs. Is it a security problem? This is from another howto:<br />
<br />
<div style="margin:20px; margin-top:5px; ">
	<div class="smallfont" style="margin-bottom:2px">Quote:</div>
	<table cellpadding="6" cellspacing="0" border="0" width="100%">
	<tr>
		<td class="ubuntu_quotebackground">
			
				fill the disk with random data (and wait many more minutes...); /dev/urandom won't be as random as /dev/random, but it is the best practical solution available:<br />
<br />
# sudo dd if=/dev/urandom of=/dev/hda3
			
		</td>
	</tr>
	</table>
</div><br />
Also there is no part where you choose the encryption algorithm. Is it AES256 by default?<br />
<br />
These may be stupid questions, but I just want to be sure <img src="http://ubuntuforums.org/images/smilies/icon_confused.gif" border="0" alt="" title="Confused" class="inlineimg" /></div>
		<!-- / message -->
		<!-- message -->
		<div class="vbclean_msgtext" id="post_message_1208971">Filing partition with random data is needed if two cases:<br />
<br />
 * you had some crucial info on the HDD before installation<br />
 * you are totally paranoid <img src="http://ubuntuforums.org/images/smilies/icon_wink.gif" border="0" alt="" title="Wink" class="inlineimg" /></div>
		<!-- / message -->
		<!-- message -->
		<div class="vbclean_msgtext" id="post_message_1208990">Several additions have been made:<br />
<ul><li>some corrections to initramfs scripts to bypass confusion with bootsplash</li>
<li>some clerifications about server/desktop installation profile</li>
</ul><br />
Howto moved to Ubuntu Comunity Documentation:<br />
<a href="https://help.ubuntu.com/community/EncryptedFilesystem" target="_blank">https://help.ubuntu.com/community/EncryptedFilesystem</a></div>
		<!-- / message -->
```




As you can see there is a starting of a message with the key tags 
**<-- message -->**
and a ending quote 
**<-- / message -->**
I would only like the 1ST message. I would like to delete everything after the 
2nd or echo the first to a new file what ever does the trick. 
Thanks I look forward to hearing from you. 
I have tried ```
sed -n '/<!-- message -->/,/<!-- \/ message -->/p' .foo.txt
```
but this is Not working is there a way to tell that to parse into its own files 

Thanks,
Joseph

---

### Post by papibe on 2012-04-12
Hi josephmills.

Does it have to be on bash? I think python can handle better string matches and substitutions. Here's my take to get the text between the tags:
```
#!/usr/bin/python

import string

source_file = "./source.htm"

try:
    fin  = open( source_file, "r" )
    data = fin.read()

except IOError:
    print "Can't open source file:", source_file
    exit( 1 )

start_match = "<!-- message -->"
end_match   = "<!-- / message -->"

start = string.find( data, start_match)
end   = string.find( data, end_match)

print data[ len(start_match) + start : end]

# Alternatively, a trimmed output:
# print data[ len(start_match) + start : end].strip()
```
Would that work for you?
Regards.

---

### Post by effenberg0x0 on 2012-04-12
Hi, you can easily go sed, or even grep to get the line #'s of the opening/closing tags occurrences to an array and then cat the lines in-between array limits using a while/for loop. But I think it's a lot easier and more "compact" with a awk one-liner.

I have saved your example content to a text-file name test.html

```
awk '/<!-- message -->/,/<!-- \/ message -->/' ./test.html | awk 'END {print $(2)}' RS= FS="\<\!-- message --\>|\<\!-- \/ message --\>"
```

On the second awk (pipe) you can improve $(2) with the NF/NR variables if you want to.
It's outputting to stdout. But you can use something like >> output.txt or, even better | tee -a at the end.

The problem I have with using bash search/match tools to parse html is that it eventually gets visually confusing, because we have to escape '/', '<', '>', etc. Most people will go C/C++ or, more commonly, python and use some html/xml lib API to navigate through the  input file tags easier. One thing you can do to make things visually easier is use tr or even sed to replace <<!-- message --> for [START] and <\!-- \/ message --\> for [END]. I think that's what I would eventually do if I wanted to go pure bash. However, just for kicks, you could also use xpath, something like:
```
xpath -q -e '<!-- message -->' -e '<!-- / message -->' test.html
```

Regards,
Effenberg

---

### Post by josephmills on 2012-04-12
Thanks A million guys !!!!!

---

