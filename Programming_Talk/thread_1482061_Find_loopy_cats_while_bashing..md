---
title: "Find loopy cats while bashing."
date: 2010-05-13
forum: Programming Talk
---

### Post by MaddMatt on 2010-05-13
Hi All, 

I need to batch import shapefiles into a geospatial database I just set up and I wrote this script to automate the process:

```

#! /bin/bash
DIR="/searchdirectory/"
SCHEMA="Basemap"
DBNAME="GIS_Database"

find $DIR -nowarn -name *.shp > /home/user/$SCHEMA.t
cat /home/user/$SCHEMA.t | while read line
do
	TABLENAME=`echo "${line}" | sed 's/.shp//' | rev | cut -d"/" | rev`	
        echo "shp2pgsql -s 32629 ${line} $SCHEMA.$TABLENAME | psql -d $DBNAME" >> /home/user/testoutput.t
done

```

but the script is getting hung up with the cut command:
> 
cut: you must specify a list of bytes, characters, or fields
Try `cut --help' for more information.


I've tried re-writing it a few different ways, but no luck. There is text in the $SCHEMA.t input file, so I think it has to do with the quotation marks in the echo statement. Anyone see my error? Thanks in advance, 

Cheers
m

---

### Post by hannaman on 2010-05-13
Cut needs to know what you want it to output.  Based on the delimiter you specified, you probably want a certain field.
```
cut -d"/" -f2
```
Will get the second field using / as a delimiter.

---

### Post by frostschutz on 2010-05-13
what's cut -d"/" supposed to do?

---

### Post by MaddMatt on 2010-05-13
> **hannaman said:**
> Cut needs to know what you want it to output.  Based on the delimiter you specified, you probably want a certain field.
```
cut -d"/" -f2
```
Will get the second field using / as a delimiter.

Thanks hannaman! That did the trick. 

> **frostschutz said:**
> what's cut -d"/" supposed to do?

The purpose of cut in this string is to isolate the filename from the directory.

Find will give me the full path (ie /home/user/someshapefile.shp), but because the path can have an unknown number of subdirectories (/home/user/somefolder/shapefile.shp, /home/user/somefolder/anotherfolder/shapefile.shp)

I used rev to reverse the string so that I know the filename will be the first field in the line delimited by "/". 

So, if find gives me:

/home/user/someshapefile.shp

```

$ echo "/home/user/someshapefile.shp" |sed 's/.shp//'
/home/user/someshapefile
$ echo "/home/user/someshapefile" |rev
elifepahsemos/resu/emoh/
$ echo "elifepahsemos/resu/emoh/" | cut -d"/" -f1
elifepahsemos
$ echo "elifepahsemos" |rev
someshapefile

```

---

### Post by hannaman on 2010-05-13
That's a lot of work to just get the filename.  Basename will do the same thing with just one command.
```
$ basename /home/user/someshapefile.shp .shp
$ someshapefile
$ basename /home/user/somefolder/anotherfolder/shapefile.shp .shp
$ shapefile
```

---

### Post by MaddMatt on 2010-05-13
> **hannaman said:**
> That's a lot of work to just get the filename.  Basename will do the same thing with just one command.
```
$ basename /home/user/someshapefile.shp .shp
$ someshapefile

```

Dang! Thanks for that one. That easily halved the run-time of the script! Way cool!

Now the script reads like this:

```

#! /bin/bash

## User Variables: ##
DIR="/searchdirectory/"
SCHEMA="YourSchema"
DBNAME="YourDatabase"
SRID="12345"
OUTPUTDIR="/home/user"

## Program Variables ##
TEMPFILE="$OUTPUTDIR/$SCHEMA.t"
OUTPUTFILE="$OUTPUTDIR/import-$SCHEMA.sh"

echo -e "#! /bin/bash\n# `date`" > $OUTPUTFILE

find $DIR -nowarn -name *.shp > $TEMPFILE
cat $TEMPFILE | while read line
do
     echo "shp2pgsql -s $SRID ${line} $SCHEMA.`basename ${line} .shp` | psql -d $DBNAME" >> "$OUTPUTDIR/import-$SCHEMA.sh"
done

chmod +x $OUTPUTFILE
rm $TEMPFILE

echo -e "Import script for:\nSchema: $SCHEMA\nDatabase: $DBNAME\noutputted to: $OUTPUTFILE\n`date`\n"

exit 0

```

Thanks!

---

