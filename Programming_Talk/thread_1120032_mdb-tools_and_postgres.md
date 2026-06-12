---
title: "mdb-tools and postgres"
date: 2009-04-08
forum: Programming Talk
---

### Post by zazuge on 2009-04-08
hello
well i have a graduation subject on witch i had to migrate from access to postgres 
the linux fanatic i am, i didn't like the idea to install windows & office again, hopefully  i found the mdb-tools thingy witch let me export schema and data to the postgres database.
well that didn't pass without some hitches
especialy the mdb-schema that generate the DDL script for the destination platform the constraint (primary&foreign keys) are not supported for postgres.
hopefully postgres syntax don't differ a lot from oracle one (witch is supported )
but multiple keys constraints are put on individual lines so i had to write a stript to generate a sql dump file ready to be executed with psql

because i'm cool i'll share it with you 
```

#!/bin/bash
# author d.abd(alias zazuge)

mdb="$1"

# generating Database schema DDL sql script
# replace simple drops with cascading  drops

##mdb-schema "$mdb" postgres |sed 's/DROP.\+/&'$(echo -e '\b\c')'\ CASCADE;/'
mdb-schema "$mdb" postgres |grep DROP |sed 's/;$/\ CASCADE;/'

echo "START TRANSACTION;"
# remove simple drops and relpace the Memo access type with ulimited Text Potgres type
mdb-schema "$mdb" postgres |sed '/DROP/d'|sed 's/Postgres_Unknown.\+,/Text,/'

# using oracle option to get the constraints (mainly Primary and Foreign Keys ones) DDL sql script
# because postgres option isn't suported for this step it just make some changes to the oracle sql script
#for x in $(mdb-schema "$mdb" oracle|grep alter  |sed 's/references\ /\n/'|sed '/alter/d'|sort|uniq);do 
#       table=$(echo $x |sed 's/(.\+//')
#       key=$(echo $x |sed 's/^.\+(//'|sed 's/)//')
# add primary key constraint (there is some problem with multiple foreign key from the same table
#       echo "ALTER TABLE $table ADD CONSTRAINT "$table"_"$key" PRIMARY KEY ($key);" 
#done
# extracting data from tables
#switch date format
# extracting data from tables
#switch date format
echo "set datestyle to 'mdy';"
for table in $(mdb-tables "$mdb") ;do
        echo "COPY "$table" ( $(mdb-export "$mdb" $table   |head -n1) ) FROM stdin;"
        mdb-export "$mdb" $table -Q -H -d'\t' |iconv -t WINDOWS-1252 |iconv -f WINDOWS-1256
        echo "\." 
done
#switch back date format
echo "set datestyle to 'dmy';"

## applying primary key constraint 
echo "------primary key constraint-----------"
for x in $(mdb-schema "$mdb" oracle|grep alter  |sed 's/references\ /\n/'|sed '/alter/d'|sort|uniq);do
        table=$(echo $x |sed 's/(.\+//');
        if [ "$otable" != "$table" ] ;then
                key=$(echo $x |sed 's/^.\+(//'|sed 's/)//');
# add primary key constraint (there is some problem with multiple foreign key from the same table
                if [ "$otable" != "" ] ;then echo "ALTER TABLE $otable ADD CONSTRAINT "$otable"_"$(echo $okey|sed 's/\,/_/g')" PRIMARY KEY ($okey);" ;fi
        else
                key="$key,$(echo $x |sed 's/^.\+(//'|sed 's/)//')";
        fi;
        otable=$table;
        okey=$key;
done
echo "ALTER TABLE $otable ADD CONSTRAINT "$otable"_"$(echo $okey|sed 's/\,/_/g')" PRIMARY KEY ($okey);" 

# add the foreign key constraint (this algorithme can't handel multiple columns foreign keys)
echo "------foreign key constraint-----------"
#mdb-schema "$mdb" oracle|grep alter |sed 's/$/;/'
# this foreignkey code is exprimental it works but not perfectly some times it cause some errors
for x in $(mdb-schema "$mdb" oracle|grep alter  |sed 's/constraint\ /\n/' |sed 's/references\ /\n/'|sed '/alter/d'|grep foreign|sort|uniq|sed 's/\ foreign key\ //');do
#       extract relation name using - as separator instead of _ because it's used in table names
#        relation=$(echo $x |sed 's/(.\+//'|sed 's/_/-/g');
        relation=$(echo $x |sed 's/(.\+//');
#       echo $relation
        if [ "$orelation" != "$relation" ] ;then
                key=$(echo $x |sed 's/^.\+(//'|sed 's/)//');
#               echo $key
## add primary key constraint (there is some problem with multiple foreign key from the same relation
#                if [ "$orelation" != "" ] ;then echo "ALTER TABLE $(echo $orelation|cut -f2 -d'_') ADD CONSTRAINT "$orelation" FOREIGN KEY ($okey) REFERENCES $(echo $orelation|cut -f1 -d'_')($okey)  ";fi
                if [ "$orelation" != "" ] ;then echo "ALTER TABLE $(echo $orelation|cut -f2 -d'_') ADD CONSTRAINT "$orelation" FOREIGN KEY ($okey) REFERENCES $(echo $orelation|cut -f1 -d'_')$(grep -i primary  dump_paie.sql |grep $(echo $orelation|cut -f1 -d'_')|sed 's/^.\+KEY\ //') ;" ;fi
#                if [ "$orelation" != "" ] ;then echo "relation=$relation orelation=$orelation key=$key okey=$okey " ;fi
        else
                key="$key,$(echo $x |sed 's/^.\+(//'|sed 's/)//')";
        else
                key="$key,$(echo $x |sed 's/^.\+(//'|sed 's/)//')";
        fi;
        orelation=$relation;
        okey=$key;
done
echo "ALTER TABLE $(echo $orelation|cut -f2 -d'_') ADD CONSTRAINT "$orelation" FOREIGN KEY ($okey) REFERENCES $(echo $orelation|cut -f1 -d'_')$(grep -i primary  dump_paie.sql |grep $(echo $orelation|cut -f1 -d'_')|sed 's/^.\+KEY\ //') ;" 
echo "COMMIT;"

exit 0


```
i left the old syntax commented for didactict purpose (or because of laziness :p )
now you have to do some little correction in the dumpfile before it works.

if someone have some suggestion or correction ^^.

---

