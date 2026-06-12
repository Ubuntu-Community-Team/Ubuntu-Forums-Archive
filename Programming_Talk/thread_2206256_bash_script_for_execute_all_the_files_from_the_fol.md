---
title: "bash script for execute all the files from the folder"
date: 2014-02-18
forum: Programming Talk
---

### Post by Monica_Bannurkar on 2014-02-18
Hello!!
 
I m fresher in Ubuntu script writing. I want to write a code which can read a file at a time, execute it and store the output in other folder.

ex: Folder input have the different sound files with wave format 
Input
abc.wav
xyz.wav
ghj.wav
huj.wav

output folder 

abc.prm
xyz.prm
ghj.prm
huj.prm

---

### Post by drmrgd on 2014-02-18
How are you generating the .prm files from the .wav files?  From what you posted, I think the simple solution is to use a for loop to iterate through all of the files you want to process.  So, assuming you have a directory full of those .wav files, and are running a program called 'prm_maker', which automatically creates the new .prm file (we need to know how the output is generated in order to better tweak the command), you could do something like this:

```

for f in *.wav; do prm_maker "$f"; done

```

That will loop through each .wav file, storing the name in the variable '$f', and then pass that to the 'prm_maker' script until there are no more .wav files to process.

Like I said, though, I don't know how the .prm files are generated, and whether or not you have to supply the new file name.  If so, you could use substitution to create the new file name.  So, suppose you have to use a redirect to create the new file name, you could do something like this:

```

for f in *.wav; do prm_maker "$f" > ${f/.wav/.prm}; done

```

Anyway, that should get you started.  Post back with details on how to generate the prm files, and we can refine the method a bit more for you.

---

### Post by Monica_Bannurkar on 2014-02-18
Thank you!!
                  I'm trying for the speaker recognition. And i m using the ALIZE for pre processing the sound signal. hence i need to write a code which takes a file at a time and perform the processing part and store it in other folder. I m facing problem in executing each sample hence i m looking for a script which can take samples from input folder one by one, process it and then put the processed data in other folder.

---

### Post by drmrgd on 2014-02-18
I had a look at the ALIZE program, and it seems very complex.  I'm not entirely sure how to use it without reading a lot of documentation.  How would you process one file at a time?

It almost seems as if you need to write a script in order to process one file at a time (or at least create some kind of parameter file).  So, you may need a wrapper script if you want to batch things.  I'm not quite sure how this works to be honest.  Maybe an example of how you process one file at a time would lead to a solution for batching files.

Otherwise, this might be too specific to the software and a better question for the maintainers of the package.

---

