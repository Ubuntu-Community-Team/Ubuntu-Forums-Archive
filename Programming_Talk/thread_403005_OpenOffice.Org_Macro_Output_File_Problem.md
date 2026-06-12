---
title: "OpenOffice.Org Macro Output File Problem"
date: 2007-04-06
forum: Programming Talk
---

### Post by a2c39a on 2007-04-06
Hi Folks,

I've written an OpenOffice.Org Macro to open a downloaded ASCII text file, process it and write the processed data to a new text file.
However I have a problem!
The input file is in ASCII (8bit) format, the output file seems to be in UNICODE (16bit) format but the extended ASCII characters (above 127) do not seem to have been correctly converted to the 2 byte format. When loaded into gEdit the French é appears as a ? in reverse video (&#65533;)!
How can I either:-
a. Keep the output file in ASCII format?
or
b. Convert the extended characters so they display correctly in Unicode?

The basis of the Macro is:-

  	iNum1 = FreeFile
  	Open "Input.File.Name.txt" For Input As #iNum1
  	iNum2 = FreeFile
  	Open "Output.File.Name.txt" For Output As #iNum2

  	Line Input #iNum1, sLine

	'Carry out processing for this line, creating sOline and then output the rebuilt line

    	Print #iNum2, sOline
	
	Close #iNum1
	Close #iNum2

I'm using Ubuntu Edgy Eft 6.10 with all latest updates and the included OpenOffice.Org suite 2.0.4

Many thanks for any help, John.

Hope this is in the right section?!

---

### Post by a2c39a on 2007-04-12
Hi Folks,

Thanks for your help.
I've found the answer to my problem is to use 'Text(encoded)' on my input file.
I copied the method shown in this thread on the OOo forum:-
[http://www.oooforum.org/forum/viewtopic.phtml?t=53813&highlight=textinputstream]("http://www.oooforum.org/forum/viewtopic.phtml?t=53813&highlight=textinputstream")

Hope this may help someone else with a similar problem.

With best wishes, John.

---

