---
title: "Extractor - Allows scripts to read data from theselves."
date: 2008-04-13
forum: Programming Talk
---

### Post by PR0M37H3U5 on 2008-04-13
Extractor is a way for scripts to read data from the themselves. Scripts store data between two tokens at the end. They can then read this data as a file and do anything they want with it. My [[COLOR="Blue"]Truewipe[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4710637")  and [[COLOR="Blue"]Randomkey[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4712303") scripts have their own user manual stored at the end of the script. They read this data and present it, when the users gives a bad flag to the program. This makes formatting much easier than using echo -e "\n blah blah blah" to print the help manual.

For example, see the print_usage command to see how the extractor script prints its manual from itself.

```
#(./extractor -id -f extractor -t @token@ will print itself!)

#extracts text between the last two tokens of a file


print_usage() 
{ $0 -d -f extractor -t @manual@ ;}

#Get Options
while getopts 'f:t:bcdies:' OPTION
do
  case $OPTION in
  f)	file=$OPTARG;;
  i)	includeTokens=1;;
  t)	token=$OPTARG;;
  b) strip+=" /^[ \t\r\n\v\f]*$/d;";;	#strip blank lines
  c) strip+="/^[ \t\r\n\v\f]*#.*$/d;s/#.*//;";;	#strip comments
  e) strip+="s/[ \t]*$//;";;	#strip trailing spaces
  s) strip+="/^[ \t\r\n\v\f]*[$OPTARG].*$/d;s/[$OPTARG].*//;";;#strip lines beginning with $OPTARG
  d) strip=" ";;			#don't strip anything
  ?)	print_usage; exit 2;;
  esac
done
shift $(($OPTIND - 1))

#Alternate Options
if [ ! $file ]; then file=$1; fi
if [ ! $token ]; then token=$2; fi

#If there is no strip commands, then use the default
if [ ! "$strip" ]; then
	eval $0 "-bce" "-f $file" "-t $token"	#Strip everything (default)
	exit 0
fi

#Get Line numbers of tokens
numbers=$(grep -n $token $file | sed 's/:.*//' | tail -n 2 )
start=$(echo $numbers | sed 's/ .*//')
end=$(echo $numbers | sed 's/.* //')

#Process Optional flags
if [ ! $includeTokens ]; then	#Default is no tokens
	start=$(($start+1))
	end=$(($end-1))
fi

#Output file
eval "sed -n '$start, $((end))p' $file | sed '$strip'"
exit 0

#Begin Data section:

@manual@
Usage:	extractor [options] file token

Required:
	-f file
	-t token
	
Optional:
	-i include tokens

Stripping:
	By default, extractor will remove comments lines, blank lines and trailing spaces
	-d don't strip anything
	-b strip blank lines
	-c strip comments (lines beginning with #)
	-e strip trailing spaces
	-s [CHARACTER] strip and line beginning with [CHARACTER]

Examples:
	#Print the section of [file between the last two tokens:	
	extractor file token	
    
	#Include the tokens and don't strip comments and blank lines:	
	extractor -id -f file -t token
	extractor -id file token
	
	#Include this into a BASH script:
	#Read data from itself and pipe it into a command:
	extractor $0 token | command

@manual@

@token@


```


Here is another example of how I use extractor. Below is a script that I use to automatically backup my files. It copies every folder that has changed in $source to the $target drive. I want to exclude certain directories, but rsync demands a file that contains a list of excluded directories. Two files would be messy so Instead, the script below will read data from itself between the two @tokens@, interpret that as a file and pipe it into the rsync command.

```

extractor $0 @token@ | rsync -var --exclude-from '-' $source/* $target

exit 0

@token@
music
movies
badfolder1
#badfolder2
badfolder3
@token@

```

---

### Post by pmasiar on 2008-04-14
Why would I want to parse source code to extract data from it if i can just define data literals and use them? For long text, Perl has HEREDOCs, Python has tripple-quoted strings. Java does not any, but that's Java. :-)

---

### Post by LaRoza on 2008-04-14
@OP You should get yourself a wiki/blog/site to host and release your scripts. This forum isn't for free advertising. If you want to post them, have them all in the same thread.

---

