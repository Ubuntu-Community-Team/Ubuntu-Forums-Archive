---
title: "A dynamic amount of files in C++?"
date: 2007-07-09
forum: Programming Talk
---

### Post by danhm on 2007-07-09
I'm trying to figure out a way to take any given amount of CSV files and combine them into one, retaining the order -- for example, if there were 3 files, my combined file would be:
file1|file2|file3,file1|file2|file3,etc

However, I can't get it working and was looking for some tips (or maybe, more appropriately some "pointers")


The code I'm using is
```

int dataFileNumber;
string inputD;

cin >> dataFileNumber;
cin >> inputD;
if(dataFileNumber<=0)
      cout << "Invalid number of data files. Must be at least 1.\n";
else if(dataFileNumber>1){
      ofstream dataFiles;
      ifstream data1, data2;
      int counter=1;
      dataFiles.open("allData.txt");
      string temp;
      while(counter <= dataFileNumber){
            data1.open(inputD.c_str());
            metafile >> inputD;
            data2.open(inputD.c_str());
		
            while(!data1.eof()){
                  getline(data1,temp,',');
                  dataFiles << temp << "|";
                  getline(data2,temp,',');
                  dataFiles << temp << ","; 
            }
            data1.close;
            data2.close;
            dataFiles.close;
            inputD = "allData.txt";
            counter++;
      }		
}	

```

---

### Post by Soybean on 2007-07-09
Ah, I see what you're trying to do there... you want to do 2 files at a time, and then use the output from one group of two as one of the inputs for the next iteration. That's not a bad idea, and some variation of that is probably your best bet if you're resource-constrained and not in a hurry. I think you'll need to do something about the filename, though... opening it for reading and also opening it for writing (a process which erases the existing file) seems prone to failure. Perhaps you could alternate between two temporary files, and then delete them at the end. Also note that your while loop closes dataFiles, then tries to write to it in the next iteration without reopening it.

Another option, depending on the size of the files, would be to read all of your files into memory one after the other, and then output them all at once. That would be much quicker, though it might get dicey if your files are really big. A std::vector<std::vector<string> > might be just the thing.

A third idea would be to try to open them all at once. Have you tried an array of ifstreams, or a std::vector<ifstream> ? I don't know if either would work. Can ifstreams be copied? If not, ifstream *pointers* definitely can. So you could go with a vector<ifstream *>, and dynamically allocate an ifstream for each file. This option would be best for a small number of large files -- I think there may be a limit on the number of files you can have open concurrently, and you'd need to watch out for that. You'd probably want to make an object to wrap this whole "array of files" thing, or things could get pretty messy.

---

### Post by nitro_n2o on 2007-07-09
If the files have pretty much the same name just pass them as ARGS to your program 
```
./my_program myfile_*.c 
``` which will give you an array of names that you can iterate over easily

---

### Post by slavik on 2007-07-09
why not do this in a shell using a cat command with redirection?

---

### Post by danhm on 2007-07-09
> **slavik said:**
> why not do this in a shell using a cat command with redirection?


It's going to be running in a Windows enviroment, and I also don't like to have my programs depend on other things being installed when possible (even though I don't think it's possible to find a Linux distro without cat, it's the principle that counts!)


I like your idea Soybean about using an array or vector -- I'm going to try that.

---

### Post by slavik on 2007-07-10
> **danhm said:**
> It's going to be running in a Windows enviroment, and I also don't like to have my programs depend on other things being installed when possible (even though I don't think it's possible to find a Linux distro without cat, it's the principle that counts!)


I like your idea Soybean about using an array or vector -- I'm going to try that.
Ahh, that makes sense ... (even though there is cp in "DOS")

I would consider nitro's suggestion, take the files as arguments and then output them one by one into the new file.

---

