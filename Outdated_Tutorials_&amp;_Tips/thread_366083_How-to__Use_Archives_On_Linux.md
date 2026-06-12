---
title: "How-to : Use Archives On Linux"
date: 2007-02-20
forum: Outdated Tutorials &amp; Tips
---

### Post by ambuj123 on 2007-02-20
USING ARCHIVES ON LINUX

Archives like tar,gzip,bzip2,rar,zip pack in a number of files in a single archive and further compresses them using various algorithms thus making the files occupy much less space as compared to original files. Linux provides a number of options for compressing the file , in the article we look at various options available under Linux and using them describing the command line tools and graphical front-ends like Ark and File-roller.
gzip (GNU Zip)

gzip can be used for compressing a single file , it is not meant for compressing entire directories as other file formats do . The default extension used bu gzip archives is (.gz) .

    gzip filename.ext 


This would create a file name filename.gz and replace the existing filename.ext file with filename.ext.gz file which is compressed gzip archive , the gzip command retains the file's attributes the modification,time stamp, access etc.

The compression level of the file can be varied by using options from 1 to 9 while compressing a file


    gzip -1 filename.ext

would compress the file quicker but with less compression.


    gzip -9 filename.ext

would compress the file slower but with more compression.

the default compression level is 6.

The file size of compressed gzip archive would depend on the original file format it would do well with a non - archived file such as txt,doc,bmp etc but would fair poorly with JPG , PNG etc which are already compressed by some algorithm.

The gzipped file can be decompressed by using the gzip -d or gunzip command at the command line.

the default file extension used by gzip archives is .gz if you want to use a different file extension it could be done by using the -S option
example : gzip -S .x filename.ext would create a archive by the name of filename.ext.x

tar ( Tape archiver )
The tar program combines a number of files and directory in a single file which then can be compressed using a gzip or bzip2 program to reduce it's file size.


    tar -cvf file.tar file1 file2 file3 file4

This would create a tar archive combining the file1 file2 and file3 into a single file the archive have the same name as the file1 since we have specified the -f option which makes tar use the first option as the filename of the archive , -c tells the tar program to create a archive and -v option displays all the background information on the screen.

    tar -cvf file.tar file1.tar file/ 

This command would create a archive named file.tar with file1.tar and file subdirectory as the content of the archive .

    tar -cvzf file.tar.gz file1 file2 file3 file/ 

This command would create a tar file consisting of the files and directory specified and then the file is compressed using the gzip program, to create a final archive file.tar.gz.

    tar -cvjf file.tar.bz2 file1 file2 file3 file/

This command would create a tar file consisting of the files and directory specified and then the file is compressed using the bzip2 program, to create a final archive file.tar.bz2

    tar -xvf file.tar

This command would extract all the files contained in the tar file file.tar

    tar -xvjf file.tar.bz2 

This command would extract all the files contained in the file file.tar.bz2 , it would first call the bzip2 program to extract the file.tar and the call tar to extract the file.tar and it's content.

    tar -xvzf file.tar.gz 

This command would extract all the files contained in the file.tar.gz , it would first call the gzip program to extract the file.tar and then call tar to extract file.tar and it's content.

If you have created the file.tar but want to add some file(s) later it can be done using the following command and using the -rf option .

    tar -rf file.tar file(s)



bzip2
The bzip2 is similar to gzip program but compresses file better and more effectively as compared to gzip program . The default extension used by bzip2 program is (.bz2) , the usage of bzip2 is very similar to the gzip program but has some additional options , which are described here .

    bzip2 -k filename.ext 

This command would create a archive of the filename.ext but would also keep a copy of the original file unlike gzip which replaces existing file with the the new archive file.
the bzip2 program also has different compression level ranging from 1 -least to 9-maximum . which can be set by using syntax like : bzip2 -1 filename.ext

bzip2 archives can be extracted by using the bzip2 -d option or by using the program bunzip2 .
RAR

RAR is another popular archive used both on windows and Linux platform , RAR archiver is available for both Linux and windows and could be obtained at [http://www.rarsoft.com/](http://www.rarsoft.com/). The rar archives end with extension .rar and became quiet famous because of high compression ratios and impressive features .

It is not installed by default with most Linux distribution since it is neither open source nor free software and because of license issues.

to extract file type the following commands assuming rar file is in the /usr/bin folder or it's path has been defined in environment variables .

    rar e filename .rar


To extract a particular file use the following command

    rar e filename.rar file-to-be-extracted

Where filename.rar is the file you are interested in extracting .

To archive all the files and directory in the presently working directory type the following command

    rar a file

where file is the name of archive you want to create .

If the file already exists then the new files are appended / added to the existing archive file and previous content of the archive is not deleted and if file with same name as one is being added exists then it is over-written in the archive.

To archive files and directory of a particular directory type the following command

    rar a file /path-to-directory-you-want-to-archive 


To view the list of files in the archive

    rar l archive.rar or rar v archive.rar

if RAR cannot extract file properly you can repair the archive file with command

    rar r archive.rar


zip

zip is one of the most popular file formats used for creating compressed files in Windows/DOS , a number of programs are available for creating zip files popular one being Info-zip and PKZIP . Since programs for handling zip files are widely available on all platforms so zip is most suitable file format for archives for sharing files between platforms.

    zip a archive file-to-be-archived

to compress a file use the following command

    zip -R archive

This command would archive the entire contents of the current directory in the file archive

    zip -r archive directory 

This command would archive entire contents of directory including all the subdirectories in filenamed archive

If you try to make archive of same name a already existing archive then zip would add the files you are specifying int the existing archive preserving the files already existing in the archive.

    unzip archive -d directory-location

This command would extract the contents of archive into the directory directory-location.

    zip -t archive 

This command would test the integrity of zip file.

You can get zip programs from the following links :

PKZip : : [http://www.pkzip.org/shareware/pkzip_unix.html](http://www.pkzip.org/shareware/pkzip_unix.html)


.lzh,.lha Archives : -

LHA was created by Haruyasu Yoshizaki in 1988 and orignally named LHarc which was later renamed to LHA , LHA is not widely used now but it was used by id Software to compress installation file of game Doom. It is still somewhat used in Japan .

    lha e archive.lzh 

This command would extract the contents of the archive.lzh in the current directory.


    lha ew = where-to-extract archive.lzh


This command would extract the content of archive.lzh in the directory where-to-extract

    lha a archive-name file 

This command would compress the file into archive with name archive-name , extension .lzh is automatically added.

If the archive already exists then the command would simply add the file to existing archive.

    lha a archive directory 

This command would compress all the files and sub-directories in the directory to a archive.lzh
For adding specific files wild cards can be used.

    lha l archive.lzh

This command would list the content of archive

    lha t archive.lzh

This command tests the integrity of archive.


The lha program can be obtained from : [http://www.linux.org/apps/AppId_476.html](http://www.linux.org/apps/AppId_476.html)


By Ambuj Varshney <blogambuj@gmail.com>

For Complete article / and similar articles visit : [http://linuxondesktop.blogspot.com](http://linuxondesktop.blogspot.com)

---

### Post by Kingfield on 2007-02-22
Nice, should help Newbies.

---

