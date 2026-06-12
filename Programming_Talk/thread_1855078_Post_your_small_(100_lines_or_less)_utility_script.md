---
title: "Post your small (100 lines or less) utility scripts and programs"
date: 2011-10-05
forum: Programming Talk
---

### Post by Warren Watts on 2011-10-05
As an amateur programmer, I get bored sometimes and set out to write little scripts (Usually in perl, but more and more in PHP lately) that teach me something new and do something useful.

Anyone have any nifty little scripts or programs they want to share?



(This is actually the refinement of a [thread I started a few years back]("http://ubuntuforums.org/showthread.php?t=1210888") and I felt yielded some interesting bits of code.)





.

---

### Post by DarkAmbient on 2011-10-05
Wrote this text-document scanner earlier this year. Actually sent it in to some php-contest, but that didn't work out to well for me.  Anyway, it iterate through all sub-folders of dir of choice, and in each sub-folder it iterate through each file. Upon texttype-file it opens them and search for your string-of-choice. On exact stringmatch or almost exact match, it echoes the path to file, and what line and # of words in.

[PHP]<?php
/*
Heed my warning:
* When plenty of sub-folders & files this
* this will be heavey for the server. 
* For me it took 1½ min to search through 
* a dir-tree with ~165.000 files.
*/
$search_string="replace";
$under_dir="/path/to/top/folder";
 
find($search_string, $under_dir);
 
function find($string, $dir) {
	$file_type=finfo_open(FILEINFO_MIME_TYPE);
 
	if(trim($string)!="" && $dir_h=opendir($dir)) {
		$files=Array();
		$sub_files=Array();
		while($file=readdir($dir_h)) {
			if($file!="." && $file!=".." && $file[0]!='.') {
				if(is_dir($dir . "/" . $file)) {
					$sub_files = find($string, $dir . "/" . $file);
				}
				else {
					if(substr(finfo_file($file_type, $dir."/".$file), 0,4)=='text') {					
						$lines=file($dir."/".$file);
						for($i=0;$i<count($lines);$i++) {
 
							$row_array=explode(" ", trim($lines[$i]));	
 
							for($n=0;$n<count($row_array); $n++) {
 
								$temp=strip_tags($row_array[$n]);
								$current_word=preg_replace("/[\s,+.-]+/", "", $temp); /* remove ,.+- characters. */
 
								$c="none";
								if(strcmp(trim($current_word), trim($string)) == 0) {
									$c="exact match";
								}
								elseif(strcmp(trim(strtolower($current_word)), trim(strtolower($string))) == 0) {				
									$c="non-exact match";
								}
								elseif(strstr(trim($current_word),trim($string))) {
									$c="exact match, but part of a string";
								}
								elseif(strstr(trim(strtolower($current_word)),trim(strtolower($string)))) {
									$c="non-exact, but part of a string";
								}
 
								if($c<>"none") {
									echo "<em>\"".$current_word."\"</em> found: ".$dir."/<b>".$file."</b>, row ".($i+1)." word #".($n+1). " [".$c."]<br>";
								}
							}
						}
					}
				}
			}
		}
		closedir($dir_h);
	}
	else {
		echo "no search string and/or not a valid directory.";
	}
}
 
?>[/PHP]

As it says commented. It's really heavy for the web-server if there is alot of files under search-dir. So have that in mind if anyone decides to try it. It's kinda nifty if you need to find a certain file containing a certain string. :)

---

### Post by Warren Watts on 2011-10-05
Nifty!

---

### Post by Warren Watts on 2011-12-11
Anyone else? (Bump!)

---

