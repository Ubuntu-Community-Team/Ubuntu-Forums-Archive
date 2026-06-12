---
title: "tar.gz bigger than its contents"
date: 2012-10-29
forum: Programming Talk
---

### Post by cannywizard on 2012-10-29
I have a script that users tar -g to make a daily incremental backup of a directory.

The basic guts of the script is

```
    thiserror=0;
    echo
    echo "###########################################"
    echo "INFO   Backing up "$directory
    echo "###########################################"

    mkdir -p "/data/tmp"$directory
    filename="/data/tmp"$directory"/"$filenameBase;
    echo "INFO   Backing up into output file" $filename
    cp $directory/backup.snar $directory/backup.snar.old
   
    if [ $reset -ne 0 ]
        then
        echo "removing the snar file <- THIS BACKUP IS NON INCREMENTAL"
        rm $directory/backup.snar # do a non-incremental backup
    fi

    tar -c -z -f $filename -g $directory/backup.snar $directory;
    filesize=$(stat -c%s "$filename");
   
    if [ $filesize -lt 204800 ]
        then
        echo "###########################################"
        echo "File to send to CASTOR too small - skipping (will send the next time)"
        echo "###########################################"
        cp $directory/backup.snar.old $directory/backup.snar
        else
   
        ssh yyy@xxx nsls -l $remotedirectory/$filenameBase
       
        if [ $? -eq 0 ]
            then
            echo "###########################################"
            echo "File of same name exists in CASTOR - not overwriting"
            echo "###########################################"
            thiserror=1;   

            else
            ssh yyy@xxx rfcp $filename $remotedirectory
            ssh yyy@xxx nsls -l $remotedirectory/$filenameBase
           
            if [ $? -ne 0 ]
                then
                echo "###########################################"
                echo "ERROR  Backup of "$directory" not confirmed in castor"
                echo "###########################################"
                thiserror=1;

                else
                echo "###########################################"
                echo "INFO   Backup of "$directory" succeeded"
                echo "###########################################"

            fi       
        fi   
    fi

    if [ $thiserror -gt 0 ]
        then
        mv $directory/backup.snar.old $directory/backup.snar
        errors=1;
    fi

   
    rm $filename # clean up after ourselves
```

But, if there are very few files to backup, the tar.gz is very big

```

computer:/tmp> du -sh backup.20121029.tar.gz
1.3M    backup.20121029.tar.gz
computer:/tmp> mkdir test
computer:/tmp> cd test
computer:/tmp/test> tar -zxf ../backup.20121029.tar.gz
computer:/tmp/test> du -sh .
40K     .

```

But weirdly, if I zip up the file again, it becomes small...
```

computer:/tmp/test> tar -czf test.tar.gz *
computer:/tmp/test> du -sh test.tar.gz
4.0K    test.tar.gz

```

any ideas?

---

