---
title: "Index script"
date: 2008-05-08
forum: Programming Talk
---

### Post by joeboentoe on 2008-05-08
Hello all, I want to make a shell script that indexes all of my files on my hard disk.

I already found that with the command "du" I get all the paths. But now I am a little bit stuck. I want each file as an entry in an mysql database table. With the columns:

"filename" "path" "size" "type"

Now, I already found how to interact with the mysql database and stuff, the only thing I need are the values for each file. Somebody can give me some hints how to retrieve the values for each file on the harddisk (or all files in some folder).

Thank you

---

### Post by kidders on 2008-05-10
Hi there,

Something like this might do the trick...```
find / -xdev -exec file -b {} \; -printf '%f\n%h\n%b\0' > index
```
It would produce a file called "index" containing null-separated records, with the fields you're looking for delimited by line breaks. There are lots of ways of doing this sort of thing, but this one seemed reasonably robust & efficient. Creating some sort of intermediate temporary file means you can re-run the SQL conversion without having to re-scan your entire filesystem, in the event you encounter problems.

Some other suggestions...

[LIST]
[*]It's worth taking a moment to consider what user you want to run your index-building command as. A reasonably privileged user would be a good idea ... but perhaps not so privileged as to allow users of your index to access file meta-information they shouldn't be allowed to see.
[*]If you're going to automate this procedure, nicing it pretty heavily might be a good idea. Something along the lines of **nice -n 19 find ...** would help reduce the performance impact of running such an I/O-intensive command in the background, while people are using your box.
[*]I wasn't quite sure what you meant by "size" and "type" in your o/p. In the method I suggested, I opted for size = the amount of disk space allocated to each file, and type = a wordy description of each file's contents. You might, for example, prefer to use the actual file length & its MIME type.
[*]When you're converting to SQL, be sure to take precautions over special characters (eg ' [apostrophe]). If, for example, you're using MySQL, you might want to pass the entire temporary index file through **sed**, and substitute \' [backslash/apostrophe] for ' [apostrophe], and so on.
[/LIST]

Anyhow, I hope that gives you some ideas.

---

### Post by joeboentoe on 2008-05-11
thank you very much, your reply was very helpful! I made a indexscript that suits my needs: It also indexes text in text files

#!/bin/bash 
ec#!/bin/bash 
echo -e "Are you sure you want to (re)index, the indexdatabase will be overwritten\n1.Yes\n2.No\nPress 1 or 2" #-e betekend dat echo speciale karakters omzet, zoals \n
read choice
check="leeg"
if [ $choice -eq "1" ];
then

	folder=$1
	#setting up indexdatabase
	wachtwoord='password'

	echo "Deleting old indexdatabase"
	mysql -uroot -p$wachtwoord -e "DROP DATABASE IF EXISTS DBindex;"
	echo "Creating new index database"
	mysql -uroot -p$wachtwoord -e "CREATE DATABASE IF NOT EXISTS DBindex;"
	echo "creating new indextable"
	mysql -uroot -p$wachtwoord DBindex -e "create table indextable( fileID INTEGER NOT NULL AUTO_INCREMENT,  name VARCHAR(200), size VARCHAR(50), type VARCHAR(50), path VARCHAR(300), text VARCHAR(1000000), primary key(fileID) );"
	
	echo "Searching files, please wait..."
	#temp=$(find $folder -name '*' -printf '"%f","%s","%y","%p",%p') #old find
	temp=$(find $folder -name '*' -printf '%f:%s:%p\n')
	#extra path zonder haaksjes want file en cat herkennen de haakjes die hier gezet worden voor 1 of andere reden niet als haakjes
	#echo $temp #debug
	echo "Start indexing, please wait.."

	IFS=$'\n';
	for lijn in $temp;
	do
		filename=$(echo $lijn | cut -d: -f1) 
		filenameEsc=$(echo $filename | sed -e 's/[",\\()]/\\&/g') #speciale tekens escapen		
		size=$(echo $lijn | cut -d: -f2) 

		pathToFile=$(echo $lijn | cut -d: -f3) 
		pathToFileDataBaseEsc=$(echo $pathToFile | sed -e 's/[",\\()]/\\&/g') #speciale tekens escapen
		
		#filetype checken
            
		check=$(file "$pathToFile" | grep "text")
	
		if [ -n "$check" ]; #-n hoeft er niet speciaal bij want is default
		then
			tekst=$(cat "$pathToFile" | sed -e 's/[",()\\]/\\&/g'); #speciale tekens escapen
			type=$(file -b "$pathToFile" | sed -e 's/[",()\\]/\\&/g')
				insertDatabase='"'$filenameEsc'"','"'$size'"','"'$pathToFileDataBaseEsc'"','"'$tekst'"','"'$type'"'

			#echo -e "wel tekst\n"$insertDatabase #debug

			mysql -uroot -p$wachtwoord DBindex -e "INSERT INTO indextable(name,size,path,text,type) VALUES($insertDatabase);" 2>>databaserrorsMetTekst
		

		else
			type=$(file -b "$pathToFile" | sed -e 's/[",()\\]/\\&/g')
			
			#echo "type="$type #debug
				insertDatabase='"'$filenameEsc'"','"'$size'"','"'$pathToFileDataBaseEsc'"','"'$type'"'

			echo -e "geen tekst\ninsertDatabase="$insertDatabase #debug

			mysql -uroot -p$wachtwoord DBindex -e "INSERT INTO indextable(name,size,path,type) VALUES("$insertDatabase");" 2>>databaserrorsZonderTekst

		fi

		teller=$((teller+1));
		echo "indexing $pathToFile"
		echo "$teller files indexed"
	done
	unset IFS
	echo "Indexing finished"

else
	echo "There will be no new index";
fi

---

