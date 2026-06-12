---
title: "compiling error when trying to install a binary"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by dqueue on 2008-08-14
Hello out there,

    Besides getting reaquainted with tetris, among the first things I've done with Ubuntu is trying to compile/install ClustalW1.83, a biocomputing program.  Unfortunately I have been running into a long list of errors when using "make" that look like this:

"
param.h:369: error: initialized element is not constant
param.h:369: error:`(near initialization for 'cmd_line_para[39].arg')
"

followed by errors that look like this:

"
interface.c: 2946: warning: incompatible implicit declaration of built-in function 'printf'
interface.cparam.h:369: error:3866: error:'nbrf_outfile' undeclared (first use in this function)
"

the last line reads:

"make: *** [interface.o] Error 1"

From reading this board and others I get the feeling that I need to install something prior to this compilation, or it may be an error by deprecation in the binary itself (to check for this possibility, are there any binaries would you suggest I try to install?). Any suggestions would be greatly appreciated!  If I need to share more information for clarity purposes please let me know.

Lastly, on behalf of all us newbies, I want to thank all of you out there who provide such an invaluable wealth of knowledge.    

Regards, 
David

---

### Post by Lord Xeb on 2008-08-14
go inside of the file you are trying to make an find "makefile.linux" and change it to "makefile" then run make and see what happens. I used make and had no problems. Please give us the commands you used to (just copy an paste everything in the terminal and put it here)

---

### Post by aaaantoine on 2008-08-14
If Lord Xeb's suggestion doesn't work, check the README and INSTALL documents for a list of required libraries.  Usually you can find these libraries in Synaptic (System -> Administration -> Synaptic Package Manager).

For example: Usually if library "foo" is required for compilation, you will find it in the repository as "libfoo-dev".  This will help you to compile the program.  You will also need "libfoo" installed to actually run the program, however.  If you can't find either "libfoo" or "libfoo-dev", you can always just search for "foo".  Chances are, it's something like "libfoo1.6".

That's my general response to the question.

---

### Post by dqueue on 2008-08-15
Hello Lord Xeb, aaaantoine, and others,

      Per Lord Xeb's instructions I changed makefile.linux to makefile, ran "make" in the appropriate directory, and unfortunately, the result was similiar to when i used "make -fx makefile.linux", or was it "make -f makefile.linux"?  At any rate, no improvement there.  Nonetheless, thank you for the suggestion and the information Lord Xeb; I am at least one step closer to an answer.

       Per aaaantoine's suggestion, I looked at the Readme that came with the tar file: sadness, badness--it was of no real help and there was no install file.  Thank you too aaaantoine.   

       I just noticed that there are 101 updates available for my computer now... maybe the answer lies in one those updates?  I'll try that I guess and see what happens.

       To reiterate a request I made in the original query, would someone recommend another useful binary that I might try to install as a test.  It appears based on Lord Xeb's experience that this problem has to do with my system/setup specifically, which trying to compile a different package would more or less unambiguously verify (does this make sense to other folks out there?).  (I apologize for not posting the entire output from the terminal, but I am dual booting and only have internet access on the windows side at this particular moment: sadness, badness again, I know.)

       Thank you again for the input, your time, and your consideration.

Happy trails,
David-lost-in-CP-MD

---

### Post by InfinityCircuit on 2008-08-15
I think you are missing a necessary development library. param.h is in libc6-dev so that's probably not the issue.

Incidentally, any reason you aren't using 2.0.9?  It has a pre-built binary for linux.  [ftp://ftp.ebi.ac.uk/pub/software/clustalw2/2.0.9/](ftp://ftp.ebi.ac.uk/pub/software/clustalw2/2.0.9/)

---

### Post by dqueue on 2008-08-15
Bing!  Infinity Circuit, right you are!  I was missing the C development libraries.  whew!  Thanks muchly!

David

---

