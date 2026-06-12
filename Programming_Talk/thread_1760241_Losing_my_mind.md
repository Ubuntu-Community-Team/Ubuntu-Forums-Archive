---
title: "Losing my mind"
date: 2011-05-16
forum: Programming Talk
---

### Post by bsharp on 2011-05-16
I'm writing a bash script that reads an rss feed, scrapes info from it and generates a SQL file that will load the info into a MySQL database already containing the title and text of the article. When I output (append really) the info I've found to the file (addFields.sql), it adds a newline character that causes MySQL to not match the title in the query to what it stored in the database. For example:
```

//the actual title of the article
Britain celebrates Charles Wesley's life, legacy

//what it should be
UPDATE....WHERE title="Britain celebrates Charles Wesley's life, legacy";

//what is actually output in addFields.sql
UPDATE....WHERE title="Britain celebrates Charles Wesley's life, legacy
";

```
I use sed to strip the XML tags out and sanitize the data, and everything there appears to be working correctly...but if there are any sed wizards (one of which I'm most certainly *not* :)) who notice a problem your help would be appreciated.

Here's my code, the part I append to addFields.sql is bolded:
```

#!/bin/bash

IFS=$'\n'

if [ -f addFields.sql ]
then
	rm addFields.sql
	touch addFields.sql
fi

for line in $(cat rss3)
do

	if [[ $line == *\<title\>* ]]
	then
		if [[ $line != *\<title\>Jan\ 2007\<\/title\>* ]]
		then
			echo "Found Article..."
			TITLE=`echo "$line" | sed s/\<title\>// | sed s/\<[/?]title\>// | sed 's/\"/\\"/g'`
		fi
	fi
	
	if [[ $line == *\<description\>* ]]
	then
		DESCRIPTION=`echo $line | sed s/\<description\>// | sed s/\<[/?]description\>// | sed 's/\"/\\"/g'`
	fi
	
	if [[ $line == *\<k:image_url\>* ]]
	then
		IMAGE_URL=`echo $line | sed s/\<k:image_url\>// | sed s/\<[/?]k:image_url\>// | sed 's/\"/\\"/g'`		
	fi
	
	if [[ $line == *\<k:byline\>* ]]
	then
		BYLINE=`echo $line | sed s/\<k:byline\>// | sed s/\<[/?]k:byline\>// | sed 's/\"/\\"/g'`
	fi
	
	if [[ $line == *\<k:keywords\>* ]]
	then
		KEYWORDS=`echo $line | sed s/\<k:keywords\>// | sed s/\<[/?]k:keywords\>// | sed 's/\"/\\"/g'`
	fi
	
	if [[ $line == *\<k:copyright\>* ]]
	then
		COPYRIGHT=`echo $line | sed s/\<k:copyright\>// | sed s/\<[/?]k:copyright\>// | sed 's/\"/\\"/g'`
	fi

	if [[ $line == *\<k:feature_image\>* ]]
	then
		FEATURE_IMAGE=`echo $line | sed s/\<k:feature_image\>// | sed s/\<[/?]k:feature_image\>// | sed 's/\"/\\"/g'`
	fi
	
	if [[ $line == *\<\/item\>* ]]
	then
		echo "Adding updated fields for "$TITLE"..."
		[B]SQL="UPDATE articles SET image_url=\"${IMAGE_URL}\",byline=\"${BYLINE}\",keywords=\"${KEYWORDS}\",copyright=\"${COPYRIGHT}\",feature_image=\"${FEATURE_IMAGE}\",description=\"${DESCRIPTION}\" WHERE title=\"${TITLE}\";" >> addFields.sql
		echo -n $SQL >> addFields.sql[/B]
	fi
done

echo "Done."

```

Thanks,
bsharp

---

### Post by bsharp on 2011-05-16
Ok, it looks like I've managed to solve this...here's my updated code with the changes highlighted.

```
#!/bin/bash

IFS=$'\n'

if [ -f addFields.sql ]
then
	rm addFields.sql
	touch addFields.sql
fi

for line in $(cat rss3)
do

	#get the title of the story
	if [[ $line == *\<title\>* ]]
	then
		#ignore the title of the rss feed
		if [[ $line != *\<title\>Jan\ 2007\<\/title\>* ]]
		then
			echo "Found Article..."
			TITLE=`echo "$line" | sed s/\<title\>// | sed s/\<[/?]title\>// | sed 's/\"/\\"/g' **| sed 's/[\n]$//'**`
		fi
	fi
	
	if [[ $line == *\<description\>* ]]
	then
		DESCRIPTION=`echo $line | sed s/\<description\>// | sed s/\<[/?]description\>// | sed 's/\"/\\"/g' **| sed 's/[\n]$//'**`
	fi
	
	if [[ $line == *\<k:image_url\>* ]]
	then
		IMAGE_URL=`echo $line | sed s/\<k:image_url\>// | sed s/\<[/?]k:image_url\>// | sed 's/\"/\\"/g' **| sed 's/[\n]$//'**`		
	fi
	
	if [[ $line == *\<k:byline\>* ]]
	then
		BYLINE=`echo $line | sed s/\<k:byline\>// | sed s/\<[/?]k:byline\>// | sed 's/\"/\\"/g' **| sed 's/[\n]$//'**`
	fi
	
	if [[ $line == *\<k:keywords\>* ]]
	then
		KEYWORDS=`echo $line | sed s/\<k:keywords\>// | sed s/\<[/?]k:keywords\>// | sed 's/\"/\\"/g' **| sed 's/[\n]$//'**`
	fi
	
	if [[ $line == *\<k:copyright\>* ]]
	then
		COPYRIGHT=`echo $line | sed s/\<k:copyright\>// | sed s/\<[/?]k:copyright\>// | sed 's/\"/\\"/g' **| sed 's/[\n]$//'**`
	fi

	if [[ $line == *\<k:feature_image\>* ]]
	then
		FEATURE_IMAGE=`echo $line | sed s/\<k:feature_image\>// | sed s/\<[/?]k:feature_image\>// | sed 's/\"/\\"/g' **| sed 's/[\n]$//'**`
	fi
	
	if [[ $line == *\<\/item\>* ]]
	then
		echo "Adding updated fields for "$TITLE"..."
		#echo "UPDATE articles SET image_url=\""$IMAGE_URL"\",byline=\""$BYLINE"\",keywords=\""$KEYWORDS"\",copyright=\""$COPYRIGHT"\",feature_image=\""$FEATURE_IMAGE"\",description=\""$DESCRIPTION"\" WHERE title=\""$TITLE"\";" >> addFields.sql
		SQL="UPDATE articles SET image_url=\"${IMAGE_URL}\",byline=\"${BYLINE}\",keywords=\"${KEYWORDS}\",copyright=\"${COPYRIGHT}\",feature_image=\"${FEATURE_IMAGE}\",description=\"${DESCRIPTION}\" WHERE title=\"${TITLE}\";" >> addFields.sql
		#echo -n "UPDATE articles SET description=\""$DESCRIPTION"\" WHERE title=\""$TITLE"\";" >> addFields.sql
		echo -n $SQL >> addFields.sql
	fi
done

echo "Done."

```

---

