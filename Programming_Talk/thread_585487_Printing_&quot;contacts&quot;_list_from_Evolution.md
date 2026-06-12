---
title: "Printing &quot;contacts&quot; list from Evolution"
date: 2007-10-21
forum: Programming Talk
---

### Post by trilobite on 2007-10-21
Hi all - 

  My mother is wanting to print out all of the "contacts" in her email (Evolution).  So, to help her out, I've coded up a small Python program which almost works - almost being the key word. 

  Here is my first version of the code which just prints the contact s to the screen (I'm testing it on my system, hence the "Andy" ) 
*** Start of code*** 
import anydbm

# Open database, creating it if necessary.
db = anydbm.open('/home/andy/.evolution/addressbook/local/system/addressbook.db', 'r')

# Loop through contents.  Other dictionary methods
# such as .keys(), .values() also work.
for k, v in db.iteritems():	
	print k, '\t', v
				
# Close when done.
db.close()
*** End of code *** 

This prints the following to the screen (I've disguised her email address) - 

PAS-DB-VERSION  0.2
pas-id-46F5B48000000000         BEGIN:VCARD
VERSION:3.0
FN:Mum
N:;Mum;;;
X-EVOLUTION-FILE-AS:Mum
EMAIL;TYPE=OTHER:my_mum@foo.net.nz
UID:pas-id-46F5B48000000000
REV:2007-09-23T00:34:08Z
END:VCARD

 Ok, looks fine (I can probably strip away the clutter with a few regexes). 

But, when I use the following bit of code to print the contacts to a file - 

*** Start of code ***
import anydbm

myfile = file("/home/andy/addresses.txt" , "w") 

# Open database, creating it if necessary.
db = anydbm.open('/home/andy/.evolution/addressbook/local/system/addressbook.db', 'r')

# Loop through contents.  Other dictionary methods
# such as .keys(), .values() also work.
for k, v in db.iteritems():	
	address = str("Key" + k + "Value" + v ) 
	myfile.write(address) 
					
# Close when done.
db.close()
*** End of code *** 

.... I get this - 
&#25931;&#20601;&#21313;&#17453;&#11586;&#17750;&#21330;&#20297;N&#24918;&#30060;&#12389;&#12846;&#2560;&#25931;&#28793;&#29537;&#26925;&#11620;&#13876;&#13638;&#13378;&#12344;&#12336;&#12336;&#12336;&#12336;&#22016;&#27745;&#25973;&#17730;&#18759;&#14926;&#17238;&#21057;&#3396;&#22026;&#21061;&#18771;&#20047;&#13114;&#12334;&#2573;&#20038;&#19770;&#28021;&#2573;&#14926;&#19771;&#28021;&#15163;&#3387;&#22538;&#17709;&#20310;&#21836;&#18772;&#20047;&#17965;&#19529;&#11589;&#21313;&#19770;&#28021;&#2573;&#19781;&#18753;&#15180;&#22868;&#17744;&#20285;&#18516;&#21061;&#25402;&#28012;&#27749;&#16502;&#27747;&#24933;&#11890;&#25966;&#11892;&#31342;&#2573;&#18773;&#14916;&#24944;&#11635;&#25705;&#13357;&#17974;&#16949;&#14388;&#12336;&#12336;&#12336;&#12336;&#3376;&#21002;&#22085;&#12858;&#12336;&#11575;&#14640;&#12845;&#21555;&#12336;&#13114;&#14900;&#14384;&#3418;&#17674;&#17486;&#22074;&#16707;&#17490;&#2560; 

Yuck..... 

So, why is this happening, and how can I fix the code so that it puts ordinary text in the file instead of this rubbish?   
Very many thanks in advance... 
- trilobite

---

