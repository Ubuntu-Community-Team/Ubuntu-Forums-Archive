---
title: "how to install pre-compiled binaries"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by stevebobby on 2011-09-28
I have downloaded precompiled binary files for the SRA toolkit from NCBI ([http://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?view=software](http://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?view=software)). I unzipped the files, but I am unsure how to complete the installation. When I type the commands to get the executables to run, the commands aren't found (probably because I haven't installed the toolkit, I just unzipped it). any suggestions?

thanks,
sb

---

### Post by anewguy on 2011-09-29
I have no use for this software, but I downloaded it and extracted it to see what to do.

I had to open a terminal window, CD to the folder containing the extracted files, then ./whatevercommandname

For example:

cd Downloads
cd sartoolkit.2.1.6-ubuntu32
./abi-dump


It appears these all take parameters, so the output from the above was:

dave@dave-MS-7576:~/Downloads/sratoolkit.2.1.6-ubuntu32$ ./abi-dump

Usage:
  ./abi-dump [options] [ -A ] <accession>
  ./abi-dump [options] <path[ path...]>

Use option --help for more information

./abi-dump : 2.1.6

dave@dave-MS-7576:~/Downloads/sratoolkit.2.1.6-ubuntu32$ 


I hope that helps!

Dave ;)

---

### Post by Dangertux on 2011-09-29
This might be helpful : [http://www.ncbi.nlm.nih.gov/books/NBK47540/#SRA_Download_Guid_B.3_Installing_the_Too](http://www.ncbi.nlm.nih.gov/books/NBK47540/#SRA_Download_Guid_B.3_Installing_the_Too)

EDIT : the above poster actually downloaded it.

---

