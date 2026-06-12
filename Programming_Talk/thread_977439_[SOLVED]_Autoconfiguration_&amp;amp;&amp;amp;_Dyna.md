---
title: "[SOLVED] Autoconfiguration &amp;amp;&amp;amp; Dynamic Automake.am loading"
date: 2008-11-10
forum: Programming Talk
---

### Post by snikrot on 2008-11-10
Hi all,

At the moment I'm having a little project. Because it involves multiple directories which don't all have automake.am I'm trying to create a autoconf/automake structure which automatically detects which directories have automake.am and according to that includes them within the parent automake.am.
I'm keeping in mind Peter Miller's [Recursive Make Considered Harmful]("http://www.pcug.org.au/~millerp/rmch/recu-make-cons-harm.html")
The result of it all has to be a project in which I can add/remove directories without changes to the parent automake.am. I only have to add a automake.am to the directory I'm adding.

The problem at the moment is within my automake file I can't seem to get automake dynamically include automake.am files. Does anyone know how to make it work?

Here's my (relevant) autoconf macro
```

##step1: get directories
##step2: check which of those directories has makefile.am
##step3: the directories which contain makefile.am are checked recursively for makefile.am
get_directories_containing_makefileam(){
	directories=$(ls -l $path_to_source | egrep '^d' | awk '{ print $9 }')
	
	#echo $directories
	
	for dir in $directories
	do
		#echo "testing directory $path_to_source/$dir"
		if test -e "$path_to_source/$dir/Makefile.am"; then
			makefileam+="$path_to_source/$dir "
			#echo "Automake.am found in dir $path_to_source/$dir added to build path";
		fi 
	done
	
	index_name="\$$index"
	
	#echo $makefileam 
	tmp=$(echo $makefileam | awk "{ print \$$index }")
	#echo $tmp
	
	#echo $index
	
	if test -d "$tmp"; then
		index=$index+1
		path_to_source=$tmp
		#echo "new path $path_to_source"
		get_directories_containing_makefileam
	fi
}

declare -i index=1
path_to_source=.
get_directories_containing_makefileam
AC_SUBST([makefiles],[$makefileam])

```

And here's my (relevant) parent automake.am
```

automakefiles=@makefiles@

$(foreach dir,$(automakefiles),$(include $(dir)/Makefile.am))

```

---

### Post by snikrot on 2008-11-11
Well solved it by just making a script create the makefile.am.

create_Makefile_Am.sh
```

##step1: get directories
##step2: check which of those directories has makefile.am
##step3: the directories which contain makefile.am are checked recursively for makefile.am
get_directories_containing_makefileam(){
	directories=$(ls -l $path_to_source | egrep '^d' | awk '{ print $8 }')
	
	#echo $directories
	
	for dir in $directories
	do
		#echo "testing directory $path_to_source/$dir"
		if test -e "$path_to_source/$dir/Makefile.am.include"; then
			makefileam+="$path_to_source/$dir "
			#echo "Automake.am found in dir $path_to_source/$dir added to build path";
		fi 
	done
	
	index_name="\$$index"
	
	#echo $makefileam 
	tmp=$(echo $makefileam | awk "{ print \$$index }")
	#echo $tmp
	
	#echo $index
	
	if test -d "$tmp"; then
		index=$index+1
		path_to_source=$tmp
		#echo "new path $path_to_source"
		get_directories_containing_makefileam
	fi
}

declare -i index=1
path_to_source=.
get_directories_containing_makefileam
###### End of function

##### Build the makefile.am
if test -e "./Makefile.am.include"; then
	cat ./Makefile.am.include > ./Makefile.am
	echo "" >> ./Makefile.am
	
	for dir in $makefileam
	do
		cat $dir/Makefile.am.include >> ./Makefile.am
		echo "" >> ./Makefile.am
	done
	
	echo "Finished creating Makefile.am"
else 
	echo "No Makefile.am.include found. Not able to create Makefile.am)"
fi
##### End of function

```

After this I can run autoconf --install and ./configure

---

