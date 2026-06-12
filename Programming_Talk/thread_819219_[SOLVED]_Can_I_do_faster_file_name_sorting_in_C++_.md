---
title: "[SOLVED] Can I do faster file name sorting in C++ than in Java?"
date: 2008-06-05
forum: Programming Talk
---

### Post by xlinuks on 2008-06-05
Hi,
I'm trying sort out (large lists of) file names (for instance from /usr/lib = 1948 files). It is important to support UTF (foreign languages like Russian), thus to keep in mind that every character in the file name might be larger than 1 char, thus to compare file names char by char I can't use in C++ something like (I tested, the app goes into random glitches if there are "unusual characters" in the file name):
> 
ustring str;

//char is only 1 byte long!
//if used - the app would work much faster
//but woldn't work correctly with UTF characters
//of other languages
char c = str[i]


but rather (tested, works without glitches):
> 
ustring str;
//ustring::value_type is 4 bytes long!
//works more slowly but supports UTF!
ustring::value_type s = str.at( i );


The question:
Here's the C++ algorithm, can anyone please suggest where I can improve it? Ironically it runs about 300% more slowly than the one I created in Java (listed below)!! I can't believe it.. I'm only learning C++ thus I hope I missed something.
In C++ it takes about 0.45 seconds to sort out and list those 1948 files, while in Java only about 0.13 seconds!

The C++ function:
```

void HFile::sortAZ( vector<HFile*> *pvFiles ) {
        int iFilesCount = pvFiles->size( );
	
	//using "ustring::value_type" instead of "char" because
	//there might/will be UTF characters larger than a "char"
	
	ustring::value_type c, c2;

        for( int i = iFilesCount - 1; i >= 0; i-- ) {

                int iCurrentIndex = i;
                HFile *pCurrentFile = pvFiles->at( i );
		//every HFile has a pre-computed "lower case file name" at creation,
		//which significantly improves performance (I tested).
		ustring str1 = pCurrentFile->getLowerCaseName( );
		//HFile has also a pre-computed count of chars in it's name
		//which slightly improves performance (I tested).
		int iStr1Length = pCurrentFile->getNameLength();

                for( int x = i; x >= 0; x-- ) {
			
                        HFile *file2 = pvFiles->at( x );
                        ustring str2 = file2->getLowerCaseName( );
                        int iStr2Length = file2->getNameLength();
                        int iLength = ( iStr1Length > iStr2Length ) ? iStr2Length : iStr1Length;

                        for( int z = 0; z < iLength; z++ ) {

                                c = str1.at( z );
                                c2 = str2.at( z );

                                if( c < c2 ) {
                                        pCurrentFile = pvFiles->at( x );
					str1 = pCurrentFile->getLowerCaseName( );
					iStr1Length = pCurrentFile->getNameLength();
                                        iCurrentIndex = x;
                                        break;
                                } else if( c > c2 ) {
                                        break;
                                }
                        }
                }

                HFile *tempFile = pvFiles->at( i );
                ( *pvFiles )[i] = pCurrentFile;
                ( *pvFiles )[iCurrentIndex] = tempFile;
        }
}

```

Java function:
```

	public static final void sortAZ( Vector<ExtFile> vFiles ) {
		int iFilesCount = vFiles.size();
		boolean bReplace = false;
		byte tLength1, tLength2;
		ExtFile currentFile = null, tempObject = null;
		String sName = null;
		
		for( int i=iFilesCount-1; i>=0; i-- ) {
			currentFile = vFiles.get( i );
			sName = currentFile.getLowerCaseName();
			tLength1 = currentFile.getNameLength();
			int iCurrentIndex = i;
			
			for( int x=i; x>=0; x-- ) {
				
				ExtFile file2 = vFiles.get( x );
				String sName2 = file2.getLowerCaseName();
				tLength2 = file2.getNameLength();
				byte iLeastStringSize = ( tLength1 > tLength2 ) ? tLength2 : tLength1;
				
				for( int z=0; z<iLeastStringSize; z++ ) {
					char c = sName.charAt( z );
					char c2 = sName2.charAt( z );
					if( c < c2 ) {
						currentFile = vFiles.get( x );
						sName = currentFile.getLowerCaseName();
						tLength1 = currentFile.getNameLength();
						iCurrentIndex = x;
						break;
					} else if( c > c2 ) {
						break;
					}
				}
			}
			
			tempObject = vFiles.get( i );
			vFiles.set( i, currentFile );
			vFiles.set( iCurrentIndex, tempObject );
			
		}
	}

```

I attached the C++ project (it's a NetBeans project).
The Java app as .jar file which contains inside the source code is at:
[http://xlinuks.googlepages.com/filemanager.jar](http://xlinuks.googlepages.com/filemanager.jar)

---

### Post by CptPicard on 2008-06-05
First thing would be to use the STL sort function instead of anything you hacked up on your own... :) Likewise, in Java, Collections.sort(...).

---

### Post by xlinuks on 2008-06-05
Would you please paste a snippet, it would take too long for me to figure out how to implement/search for what you adviced and I might not use what you suggested correctly.
I think the "Collection" sort in Java wouldn't work (as fast) in this case.

---

### Post by Zugzwang on 2008-06-05
> **xlinuks said:**
> I think the "Collection" sort in Java wouldn't work (as fast) in this case.

If I see it correctly, you are right: It will even be faster. You appear to use BubbleSort (taking O(n^2) time) whereas the sorting algorithms usually used take online O(n*log(n)) time.

More on STL sort (C++): [http://www.cplusplus.com/reference/algorithm/sort.html]("http://www.cplusplus.com/reference/algorithm/sort.html")

Your character set should be not problem since in both cases, you can write custom comparison function which will take care of that.

---

### Post by Tuna-Fish on 2008-06-05
> **xlinuks said:**
> 
I think the "Collection" sort in Java wouldn't work (as fast) in this case.

No, it will be ridiculously faster. Stop trying to micro-optimize and fix your algorithms. You are using [bubblesort]("http://en.wikipedia.org/wiki/Bubblesort"), which is O(n²), or for 1948 files, is around 4M operations. The standard one uses [quicksort]("http://en.wikipedia.org/wiki/Quicksort") (I think), which is O(n*log(n)), or for the same 1948 files, about 20k operations. That's a 200 times improvement right there.

You really should leave optimizing for later after reading a good book on algorithms. Sorry if that sounds harsh, but I have to deal daily with code written by people like you who try to finetune the loop and spend hours, if not days trying to get that last %, also making their code utterly unreadable while at it, when a simple switch to a better algorithm that is taught on any CS algorithm 1 course could get a thousand-times improvement.

---

### Post by Tuna-Fish on 2008-06-05
Oh and why it's faster in java than c++:

When you do "ustring str2 = file2->getLowerCaseName( );", unless I'm completely mistaken, you allocate memory on the heap (handled by the ustring constructor), and allocating memory is a lot slower in c++ than java.

---

### Post by NormR2 on 2008-06-05
If you were looking for sample code for sorting, here's a program that uses Collections.sort() and Arrays.sort() with some timings for 5K files. 
Not sure what the effect of Russian characters would be. Strings are Unicode and will handle most character sets.
If there are problems, perhaps you could write your own Comparator class to fix them.

---

### Post by xlinuks on 2008-06-05
Thanks a lot guys!!!
I'm now using the algorithm you suggested, I learned how to use it, and the app runs now a lot faster!!

---

### Post by slavik on 2008-06-05
IMHO, heapsort > quicksort :)

---

### Post by Tuna-Fish on 2008-06-06
and imo, mergesort > heapsort, quicksort. Yes, it takes more memory, but stable sorts ftw.

Even if you did manage to solve this problem, I still recommend picking up an algorithm book. It has plenty more than quicksort in it. In the same way you didn't realize you needed quicksort before you used it once, there are plenty other great algorithms and data structures that could solve most of your scaling and performance problems if you knew about them.

---

### Post by xlinuks on 2008-06-06
You are so right, as I have time I definitely will, for now I'm willing to get faster to know C++ to do what Java doesn't, which was pretty frustrating. I created a nice/fast Java file manager, it was done by about 80%, but in the end I decided to give up due to Java's limited features compared to what I need to create a first-class desktop app (a file manager that will solve for me and a lot of other people the "Nautilus" problem). After I finish it I'll learn some 3D/OpenGL (perhaps Glut) and mathematics - if I'm very lucky. So far things go well, and I'm delighted by the fast startup of the fm, very small memory footprint and the (file system) features I can access from C++ compared to what I had in Java!!

---

### Post by slavik on 2008-06-06
> **Tuna-Fish said:**
> and imo, mergesort > heapsort, quicksort. Yes, it takes more memory, but stable sorts ftw.

Even if you did manage to solve this problem, I still recommend picking up an algorithm book. It has plenty more than quicksort in it. In the same way you didn't realize you needed quicksort before you used it once, there are plenty other great algorithms and data structures that could solve most of your scaling and performance problems if you knew about them.
in that case, smoothsort (it's a stable heapsort) :)

---

