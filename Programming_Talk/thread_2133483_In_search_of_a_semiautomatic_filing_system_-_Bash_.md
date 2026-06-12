---
title: "In search of a semiautomatic filing system - Bash newbie"
date: 2013-04-08
forum: Programming Talk
---

### Post by gefalu2008 on 2013-04-08
I use PDF printing to collect news items and other articles. Consequently I have saved about 1500 files in my &#8216;PDF&#8217; folder. At times I move some of these files to directories that are organized by topic. In my home directory there are about 8 directories and within those altogether 1000 subdirectories from which to choose.

An automatic filing system would be ideal solution, but to my knowledge no such software is freely available for Linux. Perhaps it is possible to develop software for organizing files? From what I have heard, Python might be a good environment because it seems to have properties that are well suited for dealing with strings. However, programming is new to me. At this point I do not want to learn Python. 

I have settled for Bash programming and will be satisfied with what is feasible there. That is why what follows is an exercise in Bash programming. Please remember, I am a newbie, and your comments and suggestions are most welcome. I suppose the code I develop here can be made more efficient. And there may be bugs I do not see.

In order to define which files should go into which folders I shall use file names. I shall generate a list of files to be relocated and a list of possible destination directories. I shall compare the names of files to be transferred with the names of files that are already located in the destination folders. 

**The goal**

My aim is to generate text file &#8216;transferlist.txt&#8217; that contains a list of &#8216;mv&#8217; commands telling which documents should be moved into which directories:

```
mv "Vibrations Turn Water Into Hydrogen.pdf" "/home/user/700 Energy/Hydrogen&#8221;
mv "What Synaptic Package Manager can do.pdf" "/home/user/300 Computers/Linux/Synaptic&#8221;
etc.
```

When the properties of &#8216;transferlist.txt&#8217; are changed so that it can be run as a program, it can be executed simply by using the command

```
sh transferlist.txt
```

**Listing files and possible destinations**

We shall start by preparing a list of files in the &#8216;PDF&#8217; folder. The aim is to uses this list &#8216;pdffiles.txt&#8217; located in the ~/Test directory to indicate which files are to be moved files to other destinations. For clarity let me point out that in addition to pdf files there are other types of files in the PDF folder as well.

(The following scripts have been edited on the basis of suggestions received to this post.)

```

#!/bin/bash

# The list of files 'pdffiles.txt' that are to be moved to other destinations.

for f in ~/PDF/*; do
    [[ -e $f ]] || continue
    echo $f >> ~/Test/pdffiles.txt
done

# List the most potential destination directories - those that have at least 2 pdf files in them.
# The list below does not contain any hidden folders. 
find ~/ \( ! -regex '.*/\..*' \) -type d -exec sh -c 'set -- "$0"/'*.pdf'; [ $# -gt 1 ]' {} \; -print >> ~/Test/folders1.txt

# Edit folder pathnames so that individual words are separated for future matching with files

while read -r UneditedFolderLine 
do 
# The next 2 lines remove slashes (&#8216;/&#8217;) and underlinings to separate words in folder pathnames
Wordsseparated1=${UneditedFolderLine//\//" "} 	
Wordsseparated=${Wordsseparated1//_/" "} 

# Not all directories are intended to be destinations for file transfers.
for Folderword in $Wordsseparated 
	do 
		case "$Folderword" in
		*Music*|*Pictures*|*Calibre*|*PDF*)
		Warning="On"
		break
		;;
		*)
		Warning="Off"
		;;
		esac
	done	

if 
[ "${Warning}" = Off ] 
then 
echo "$UneditedFolderLine" >> ~/Test/folders2.txt 
fi 
done < ~/Test/folders1.txt # This file was input for the previous set of operations.

# Sort the list of directories alphabetically:
sort -d ~/Test/folders2.txt > ~/Test/folders3.txt

# Sort the list on the basis of length, ascending, producing the final list of destination folders:
cat ~/Test/folders3.txt | awk '{ print length, $0 }' | sort -n | cut -d" " -f2- > ~/Test/folders4.txt

``` 

So the key results of the first script are &#8216;pdffiles.txt&#8217; listing the files to be moved and &#8216;folders4.txt&#8217; listing potential destinations. Next we shall find matches between lines of these two documents.


**Matching the names of files to be transferred and files already in destination folders**

So we have a list of files to be transferred, &#8216;pdffiles.txt&#8217;, and a list of possible destinations, &#8216;folders.txt&#8217;. The code below generates &#8216;transferlist.txt&#8217; on the basis of matching words in filenames. 

For each file to be moved the code builds an index. The code visits every possible destination folder and sees how many times the words in the filename match words in the filenames of files in the destination folder. The folder that gets the highest index is selected to become the destination of the file to be transferred.

So here we go. 

```

#!/bin/bash 

# Start by reading the list of documents (pdffiles.txt) to be moved
while read -r Filerow 
do 
Index=0 # Index counts matches between words. Set it to zero.
SoFarBestIndex=0 
TheBestFolder=aa
SoFarBestFolder=bb 

	for Fileword in $Filerow # Taking each word in the name of the file
	do 
		if [ "${#Fileword}" -lt 4 ] ||  # except those words that are shorter than 4 characters
		[[ "${Fileword}" = *[[:digit:]]* ]] # or contain digits.
		then 
			continue 
			else 

# Next read the list of destination folders from file folders.txt
			while read -r UneditedFolderrow 
			do 
			Index=0 # Index counts matches between words. Set it to zero.
			for FileInFolder in "$UneditedFolderrow"/* 
			do 
			[ ! -f "$FileInFolder" ] && continue

# Next let us chop the names of files in the folder into separate words
			FileInFolder1=$(basename "$FileInFolder")
 FileInFolder2="${FileInFolder1%.*}" # Now the words are separated and file endings deleted.

					for WordinFileInFolder in $FileInFolder2 
					do 

			if [ "${#WordinFileInFolder}" -lt 4 ] || [[ "${WordinFileInFolder}" = *[[:digit:]]* ]] ; then 
				continue 
				else 
				if [ "$WordinFileInFolder" = "$Fileword" ] # If there is a match, 
				then 
				let "Index += 1" # then add 1 to the Index.
				fi 
			fi 
				done 
					FolderrowIndex=$Index # Setting the index for the folder as a whole
			done 
				if [[ $FolderrowIndex -gt $SoFarBestIndex ]] 
				then 		 
				SoFarBestFolder="$UneditedFolderrow" 
				SoFarBestIndex=$FolderrowIndex 
				fi 
				Index=0 # Even if the $UneditedFolderrow is not the best match, the Index has to be set to zero.
			done < /home/user/Test/folders4.txt # The file containing destination directories.
TheBestFolder="$SoFarBestFolder" 

		fi 
	done 
	if [ "${TheBestFolder}" != "aa" ] && [ "${TheBestFolder}" != "bb" ]; then 
	echo "mv" \"$Filerow\" \"$TheBestFolder\" >> /home/user/Test/transferlist19.txt 
	else 
# List files that found no matching destinations:
	echo "mv" \"$Filerow\" \"\/home\/user\/PDF1\" >> /home/user/Test/orphans19.txt 

	fi 
done < /home/user/Test/pdffiles.txt # The file listing files to be transferred.


```

My computer has an Intel i5-3550 CPU and 8GiB of memory. Nevertheless, my original effort trying to match 1500 files with 1000 destination directories was too much. The bash script killed itself after running some 6 hours. I have now edited the script above and it runs much more smoothly, allowing me to multitask without any problems.

I am not quite sure if the indexing part is accurate. I have tried to test it the best I can, but my logic fails to confirm the accuracy of the code. Do you see any mistakes?

Anyway, don&#8217;t you think that this is a proof of concept for a semiautomatic filing system? Isn&#8217;t that something any file addict needs.

---

### Post by schragge on 2013-04-08
```
ls > ~/pdffiles.txt
```This won't work if any of file names contain embedded newlines. An unlikely situation to be sure, but not impossible.
See [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)
At least, hide control characters in file names with *ls -q*.

> I want to exclude directories that contain music, pictures or Calibre files. I'd probably use a case statement for this
```

case $folder in
*Music*|*Pictures*|*Calibre*);;
*) # commands adding folder to the list
  ;;
esac

```

> Finally I sorted the list of folders on the basis of line lenth, ascending: Consider
```

while read -r folder
do printf '%d\t%s\n' ${#folder} "$folder"
done < folders2 | sort -n | cut -f2-

```
As to the last script, assigning a weight to each folder in order to find the best fit for files of certain kind reminds me of mail filtering tools in the fold of *procmail*. Have you looked into possibility of using something like [crm114]("http://manpages.debian.net/cgi-bin/man.cgi?query=crm") for this?

Also, looping over every file for every destination folder is very inefficient. Just matching 1500 files with 1000 folders means the inner loop must be executed 1,500,000 times. And you're trying to match each word in the names of source files with each word in the names of files already in destination folders. Although bash offers some features that could help here (hint: associative arrays), I don't think a shell script is the right tool for the job.

---

### Post by gefalu2008 on 2013-04-09
schragge,

thank you very much! I shall test these ideas. I suppose at least the idea of using the case statement would make the code a little bit more efficient.

You are right about the huge amount of looping the script requires. That can be reduced by cutting manually the list of files  into shorter parts. 

I am only starting with bash and know no other programming languages. Is there any way to make the script stop and liberate memory and/or processor capacity after some cycles? I would not mind if the process took much longer to complete, as long as the script would not take up all memory and the full capacity of one processor core.

---

### Post by steeldriver on 2013-04-09
I wonder if you might get some efficiency improvements by building lookup tables for the terms in the directory names using bash's *associative arrays*? for example, if we shamelessly steal this fragment from a poster on stackoverflow

[http://stackoverflow.com/questions/3685970/bash-check-if-an-array-contains-a-value/14550606#14550606](http://stackoverflow.com/questions/3685970/bash-check-if-an-array-contains-a-value/14550606#14550606)

> 
If you need performance you don't want to iterate over your array repeatedly.

In this case you can create an associative array (hash table, or dictionary) that represents an index of that array. I.e. it maps the array element into its index in the list::

```
make_index () {
  local index_name=$1
  shift
  local -a value_array=("$@")
  local i
  # -A means associative array, -g means create a global variable:
  declare -g -A ${index_name}
  for i in "${!value_array[@]}"; do
    eval ${index_name}["${value_array[$i]}"]=$i
  done
}
```Then you can do something along the lines of

```

$ echo $dir1
/home/user/700 Energy/Hydrogen
$ echo $dir2
/home/user/700 Water/Hydrogen
$
$ dir1terms=( ${dir1//// } ); dir2terms=( ${dir2//// } )
$
$ for term in ${dir1terms[@]}; do echo "$term"; done
home
user
700
Energy
Hydrogen
$
$ make_index dir1lookup "${dir1terms[@]}"
$ make_index dir2lookup "${dir2terms[@]}"
$
$ filename="Vibrations Turn Water Into Hydrogen"
$ fileterms=( ${filename//// } )
$
$ count=0; for term in ${fileterms[@]}; do test "${dir1lookup[$term]}" && ((++count)); done; echo $count
1
$ count=0; for term in ${fileterms[@]}; do test "${dir2lookup[$term]}" && ((++count)); done; echo $count
2
$
```

You could probably modify that to use the array index itself to weight the values in favor of matches higher (or lower) in the directory tree if you wanted. You could do something similar in python with 'dictionaries'.

---

### Post by gefalu2008 on 2013-04-09
steeldriver,

thank you very much! This talk of associative arrays makes my palms sweat - is it fear, is it eager anticipation? It will take days for me to apply this idea, but I shall try.

Meanwhile I found two snippets of script that (when combined as below) might help me to shorten the list possible destination directories. I hope the following script lists only those directories that already have at least one pdf file in them:

```
find ~/ \( ! -regex '.*/\..*' \) -type d -exec sh -c 'set -- "$0"/'*.pdf'; [ $# -gt 0 ]' {} \; -print >> /home/user/folders.txt
```

I do not want to end in a situation where the code would list folders that have *either* zero *or* at least one pdf file.

---

### Post by Vaphell on 2013-04-10
that line won't work too well, because (unless you enable nullglob) unmatched glob will simply degrade to literal '*.pdf' and each dir will pass [ $# -gt 0 ] test.

try [ -f "$1" ] instead or simply run find -iname '*.pdf' and trim the filename part, along the lines of

```
while read f; do echo ${f%.[pP][dD][fF]}; done < <( find -iname '*.pdf' ) | sort -u
```
if number of dirs is much greater than number of pdfs this should be faster.

---

### Post by gefalu2008 on 2013-04-10
Vaphell,

thank you for joining the effort! You are right:

> **Vaphell said:**
> that line won't work too well, because (unless you enable nullglob) unmatched glob will simply degrade to literal '*.pdf' and each dir will pass [ $# -gt 0 ] test.

That line seems to produce a full list of *all* of my directories. I obtained considerable improvement by using

```
find ~/ \( ! -regex '.*/\..*' \) -type d -exec sh -c 'set -- "$0"/'*.pdf'; [ $# -gt 1 ]' {} \; -print >> /home/use/folders.txt
```

It seems that this line produces a list of directories that have at least 2 (i.e., ** -gt 1**) pdf files in them. In addition to the pdf files, there may be subdirectories as well.

I tried your suggestion, attempting to produce a list 'folders.txt' as follows:

```
while read f; do echo ${f%.[pP][dD][fF]}; done < <( find -iname '*.pdf' ) | sort -u >> /home/user/folders.txt
```

and what I got was a list of all on my pdf files, it seems. But maybe I did something wrong here.

What I would like to have is a list of all directories that have pdf files in them. (And why not doc, txt, and odt files as well).

In any case, your comments were welcome. I found an improvement, and I needed a break from associative arrays.

---

### Post by Vaphell on 2013-04-10
lol, i must have been unconscious when i wrote that line, it only strips extensions

```
$ f=/some/dir/and/then/some/file.pdf
$ echo ${f%.[pP][dD][fF]}   # this strips only extension
/some/dir/and/then/some/file
$ echo **${f%/*}**    # this strips everything from the last / (leaves dir)
/some/dir/and/then/some
```

try [ -f "$1" ], in case $1 stores unmatched glob it will be false (no file called '*.pdf'), legit file will return true and number of params doesn't matter.

---

### Post by steeldriver on 2013-04-10
> **gefalu2008 said:**
> steeldriver,

thank you very much! This talk of associative arrays makes my palms sweat - is it fear, is it eager anticipation? It will take days for me to apply this idea, but I shall try.

I hope I haven't sent you down a rabbit hole with that suggestion - I like playing with this kind of stuff but I am by no means an expert

I do encourage you to take a look at python - it has a quite expressive syntax for this kind of processing - for in example you could make a 'dictionary of dictionaries' perhaps keyed on the directories' inode values and then loop over that returning a [sorted] list of the members with the best match(es). I'm not sure if bash's arrays can be nested in that way.

I haven't really looked at your code in detail but another thing that comes to mind from the point of view of performance is whether you have found a way to implement some kind of pruning i.e. if you are searching for $term and you don't find it in /path/to/dir/to/subdir then you know right away there's no point searching for it again in /path/to/dir or /path and so on

Good luck and keep us posted with your progress

---

### Post by Vaphell on 2013-04-10
+1 on exploring python. Managing tons of data is a chore in shells, even with associative arrays in bash
easy transformation of lists and dictionaries is built right into the language

---

