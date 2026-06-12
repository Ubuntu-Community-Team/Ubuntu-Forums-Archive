---
title: "Installing an outdated package"
date: 2012-08-24
forum: Packaging and Compiling Programs
---

### Post by nbhagwat on 2012-08-24
Hi Folks,
First of all, I am a dumbass Biologist who has bitten off more than he can chew. So please be kind. I am trying to install software that was written in 2006. I am trying to compile and install it on an old Macbook 1,1 running 12.04. To satisfy dependencies, I had to install another software called Ramp (it's a proteomics software).This package contains all .cpp files. Now, coming back to the original software: The readme told me to edit the Makefile to point to the ROOT directory of the dependencies (Ramp and GSL). I did that. But when I try to compile, it tells me that a target does not exist:
```
make: *** No rule to make target `/base64.o', needed by `main'.  Stop.
```
Please help.

---

### Post by houseworkshy on 2012-08-24
I looked for proteomics in the software repositories and found  mMass, it has a website here  [http://www.mmass.org](http://www.mmass.org)  I've no idea if this would be any use to you.  That's an aside. I'm no expert on compileing but guessing that this is probably work/study related, therefore perhaps urgent, and not seeing any replies yet thought that I'd bump the thread.  Good luck.

---

### Post by nbhagwat on 2012-08-24
Thanks for the bump. unfortunately mmass won't work. This is a very niche software some guy developed in 2006. But it will get my job done. Hope someone can help.

---

### Post by 2F4U on 2012-08-25
This is just a wild guess, but is it possible that your Ubuntu installation is 32 bit and the compiler requires 64 bit libraries?

---

### Post by oldos2er on 2012-08-25
Moved to Packaging and Compiling Programs.

Could you provide a link to the software you're trying to compile?

---

### Post by nbhagwat on 2012-08-25
Here's the link:
[http://summon.sourceforge.net/download.html](http://summon.sourceforge.net/download.html)

Thanks.

---

### Post by nbhagwat on 2012-08-25
I don't know. It didn't say so in the requirements. I'll try to find out.

---

### Post by SevenMachines on 2012-08-26
My guess is that base64 has now been renamed ramp_base64, try renaming tose references in Summon's Makefile

---

### Post by nbhagwat on 2012-08-27
OK, so the trouble, from what I have found out so far, seemed to be that the SUMmOn looks for .c files and cannot use .cpp files. So I found and downloaded an older version of ramp which uses .c files. So here's the error I am getting now. Any ideas?
```
In file included from PeaksUtils.cpp:25: PeaksUtils.hpp:29:18: error: ramp.h: No such file or directory 
PeaksUtils.hpp:32:18: error: ramp.c: No such file or directory 
In file included from PeaksUtils.cpp:25: PeaksUtils.hpp:51: error: ‘RAMPFILE’ has not been declared 
PeaksUtils.hpp:51: error: ‘ramp_fileoffset_t’ has not been declared 
In file included from PeaksUtils.cpp:25: 
PeaksUtils.hpp:52: error: ‘RAMPFILE’ has not been declared 
PeaksUtils.hpp:52: error: ‘ramp_fileoffset_t’ has not been declared 
PeaksUtils.hpp:53: error: ‘RAMPFILE’ has not been declared 
PeaksUtils.hpp:53: error: ‘ramp_fileoffset_t’ has not been declared 
PeaksUtils.hpp:65: error: ‘RAMPFILE’ has not been declared 
PeaksUtils.hpp:65: error: ‘ramp_fileoffset_t’ has not been declared 
PeaksUtils.cpp:38: error: ‘RAMPFILE’ has not been declared 
PeaksUtils.cpp:38: error: ‘ramp_fileoffset_t’ has not been declared 
PeaksUtils.cpp:55: error: ‘double PeaksUtils::calculateTIC’ is not a static member of ‘class PeaksUtils’ 
PeaksUtils.cpp:55: error: ‘RAMPFILE’ was not declared in this scope 
PeaksUtils.cpp:55: error: ‘rampFile’ was not declared in this scope 
PeaksUtils.cpp:55: error: ‘ramp_fileoffset_t’ was not declared in this scope 
PeaksUtils.cpp:55: error: ‘pScanIndex’ was not declared in this scope 
PeaksUtils.cpp:55: error: expected primary-expression before ‘int’ 
PeaksUtils.cpp:55: error: expected primary-expression before ‘int’ 
PeaksUtils.cpp:55: error: expected primary-expression before ‘int’ 
PeaksUtils.cpp:55: error: initializer expression list treated as compound expression 
PeaksUtils.cpp:56: error: expected ‘,’ or ‘;’ before ‘{’ token make: *** [PeaksUtils.o] Error 1 
```

---

### Post by nbhagwat on 2012-08-27
It's true that the new version has ramp_base64. I'll try that as well on a different system. Good thing I am trying this with two systems simultaneously. (ok, maybe that's really stupid, but whatever.)

---

### Post by SevenMachines on 2012-08-27
Just to be clear, the suggestion I made works on 12.04, with a few header updates (<cstdlib> and <cstring> may need added in a few files). The binary appears to work but then I haven't tested it to any real extent

---

### Post by nbhagwat on 2012-08-27
Oh, so you got SUMmOn to work? That's brilliant! Never mind testing it, I can't even get it to compile. Did you just edit the Makefile to show ramp_base64? Could you please tell me exactly what to do?
Thanks.

---

### Post by nbhagwat on 2012-08-28
> **SevenMachines said:**
> Just to be clear, the suggestion I made works on 12.04, with a few header updates (<cstdlib> and <cstring> may need added in a few files). The binary appears to work but then I haven't tested it to any real extent

I tried what you recommended, but still get the same response. Here's the Makefie:
```
# put here the name of c++ compiler
CPPC=g++
CC=gcc

# Enable for profiling. 
#CCOPT=-pg

# put here the complete path to the RAMP include directory
RAMPINC= -I. -I/usr/local/src/ramp

# put here the complete path to the gsl include directory
GSLINC= -I. -I/usr/include/gsl

# here again the name of the c++ compiler
LD=g++

#Dynamic
LDFLAGS= -L/usr/lib -L${GSLROOT}/.libs -L${GSLROOT}/cblas/.libs -lgsl -lgslcblas -lz -lm
#Static
#LDFLAGS= /usr/lib/libgsl.a -static

OLD = 

# lfs support
LFSFLAGS= -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE

__DEBUG=1

######################################################################
#
# do not edit past this point
#
######################################################################

OBJS = InOut.o quantitation.o PeaksUtils.o IonGenerator.o \
	Modifier.o SumoAnalysis.o Digestion.o Masses.o\
	${RAMPROOT}/ramp_base64.o	${RAMPROOT}/ramp.o main.o 
 
OBJS_LNK = InOut.o quantitation.o PeaksUtils.o IonGenerator.o\
	Modifier.o SumoAnalysis.o Digestion.o Masses.o\
	ramp_base64.o ramp.o main.o

#
# rules
#
.SUFFIXES:	.o .cpp

.cpp.o:	
		$(CPPC) $(LFSFLAGS) $(OLD) $(DEBUG) $(RELEASE) $(CCOPT) ${RAMPINC} $(GSLINC) -Wno-deprecated -c ./ $<

.SUFFIXES:	.o .c

.c.o:	
		$(CC) $(LFSFLAGS) $(OLD) $(DEBUG) $(RELEASE) $(CCOPT) ${RAMPINC} $(GSLINC) -Wno-deprecated -c ./ $<


#
# targets
#
all : main 

main : $(OBJS)
	$(LD) $(DEBUG) $(CCOPT) -o summon $(OBJS_LNK) $(LDFLAGS)
	#$(LD) $(DEBUG) -O3 -o summon $(OBJS) $(LDFLAGS)

clean:
	rm -f *.o $(EXE) core

debug:
	DEBUG='-ggdb -Wall -O0'  make all

release:
	RELEASE='-O3' make all
#
# dependencies
#
Masses.o: Masses.cpp Masses.hpp
InOut.o: InOut.cpp InOut.hpp
quantitation.o: quantitation.cpp quantitation.hpp
PeaksUtils.o: PeaksUtils.cpp PeaksUtils.hpp
IonGeneratoro.o: IonGenerator.cpp IonGenerator.hpp
Modifier.o: Modifier.cpp Modifier.hpp
SumoAnalysis.o: SumoAnalysis.cpp SumoAnalysis.hpp
Digestion.o: Digestion.cpp Digestion.hpp
ramp_base64.o: ${RAMPROOT}/ramp_base64.cpp ${RAMPROOT}/ramp_base64.h
ramp.o : ${RAMPROOT}/ramp.cpp  ${RAMPROOT}/ramp.h
main.o: main.cpp 
```

I don't know what I am doing wrong.
Thanks for your help.

---

### Post by nbhagwat on 2012-08-28
Additionally, here's the main.cpp file that is looking for the ramp_64.o file:
```
/**********************************************************************

        SUMmOn 1.0 Automated identification of complex
        post translational modifications by mass spectrometry.

        Copyright (C) 2006 Patrick Pedrioli

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License along
with this program; if not, write to the Free Software Foundation, Inc.,
51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
 
************************************************************************/


#include <climits>
#include <iostream>
#include <fstream>
#include <string>
#include <stdlib.h>
#include <exception>
#include "ramp.h"
#include "quantitation.hpp"
#include "PeaksUtils.hpp"
#include "Modifier.hpp"
#include "SumoAnalysis.hpp"
#include "Masses.hpp"


int usage()
{
  cout << "Usage SUMmOn -c <condition file> <input file name>\n";
  return 0;
}


int main( int argc , char* argv[] )
{
  int	scanNum;
  int	argNum;
  int	fileNum = 2;
  int	requestedMsLevel;
  int	iAnalysisFirstScan, iAnalysisLastScan;
  bool	doReverse = true;
  double        fragmentationModificationMass;
  char* conditionFileName = NULL;
  vector<scanAnalysis> vScan;
  vector<double> mass;
  vector<double>::iterator pos;
  typedef pair<float,float>	ff;
  typedef vector< ff >	vff;
  vff	peaks;
  InOut IO;
  PeaksUtils PU;
  RAMPFILE  *pFI;
  ramp_fileoffset_t  indexOffset;
  ramp_fileoffset_t  *pScanIndex;
  struct ScanHeaderStruct scanHeader;

  // Check arguments
  if ( argc < 3 )
    {
      usage();
      exit(0);
    }

  for( argNum = 0 ; argNum < argc ;  argNum++ )
    {
      if( strstr( argv[argNum] , "-c" ) )
	{
	  argNum++;
	  conditionFileName = argv[argNum];
	  argNum++;
	  fileNum = argNum;
	  break;
	}
    }

  // Try reading reagent masses from condition file
  if( conditionFileName )
    {
      if( IO.getConditionsFromFile( conditionFileName ) )
	{
	  cout << "Could not extract conditions from " << conditionFileName << ".\n"
	       << "Please make sure that the file exists and is correctly formatted.\n";
	}
    }
  else
    {
      cout << "Could not read conditions.\n";
    }

  Quantitation Quant( IO );
  requestedMsLevel = IO.getRequestedMsLevel();
  
  for(  ; fileNum < argc ; fileNum++)
    {
#ifdef DEBUG
      cout << "Analyzing file " << argv[fileNum] << endl;
#endif   

      // Set the name of the file we are currently analyzing in the InOut class
      IO.setMzXmlFile( argv[fileNum] );

      // create an object to read this file
      if ( (pFI = rampOpenFile( argv[fileNum] )) == NULL)
	{
	  cout <<  "Could not open input file " << argv[fileNum] << endl;
	  exit(1);
	}
      
      if( (indexOffset = getIndexOffset( pFI )) == -1 )
      {
	cout << "Could not locate indexOffset\n";
	exit(1);
      }
      
      iAnalysisLastScan = 1;
      if( (pScanIndex = readIndex( pFI , indexOffset, &iAnalysisLastScan )) == NULL )
	{
	  cout << "Could not read mzXML index\n";
	  exit(1);
	}
      
      iAnalysisFirstScan = 1;

      mass = IO.getMass();
      fragmentationModificationMass = 0;
      for( pos = mass.begin() ; pos != mass.end() ; pos++ )
        {
          fragmentationModificationMass += *pos;
        }
      
          // Prepare the arrays with the amino acid masses
      Masses   atomicMasses( IO.getPrecursorMassType() , IO.getFragmentationMassType() );
      atomicMasses.addStaticModifications( IO.getStaticModifications() );

      Digestion Dg( "subDB.fasta" );
      Dg.setMassAA( atomicMasses.getMassPrecursorAA() );
 
      Modifier Mod( IO , pFI , pScanIndex  , atomicMasses , Dg , IO.getPrecursorModificationMass() , fragmentationModificationMass , "forward" );
      SumoAnalysis Sa( IO , pFI , pScanIndex , Mod );
      Sa.setLastScan( iAnalysisLastScan );
      Sa.setFirstScan( iAnalysisFirstScan );

      // Reverse search first
      if( !mass.empty() && doReverse )
	{
	  cout << "Calculating reverse modification scores." << endl;
	  
	  IO.reverseMass();
	  Modifier ModRev( IO , pFI , pScanIndex , atomicMasses , Dg , IO.getPrecursorModificationMass() , fragmentationModificationMass , "reverse" );

	  for( scanNum = iAnalysisFirstScan ; scanNum <= iAnalysisLastScan ; ++scanNum )
	    {
	      readHeader(pFI, pScanIndex[scanNum], &scanHeader);
	      if( scanHeader.msLevel == requestedMsLevel && (scanHeader.peaksCount > 1) )
		{
#ifdef DEBUG
		  cout << "Analyzing scan " << scanNum << endl;
#endif 
		  ModRev.generateMic( scanNum );
		}
	    }    
      
	  vScan = ModRev.getScanRes();
          ModRev.resetVScan();
	  Sa.setScanRes( vScan );
	  Sa.scoreMod();
	  Sa.setScanReverse();
	  Sa.resetVScan();
	}


      // And now the forward search
      if( !mass.empty() && doReverse )
	{
	  cout << "Calculating forward modification scores." << endl;
	  IO.reverseMass();		// THIS YOU NEED ONLY IF YOU ARE DOING THE 
					// REVERSE SEARCH FIRST !!!!
	}

      for( scanNum = iAnalysisFirstScan ; scanNum <= iAnalysisLastScan ; ++scanNum )
	{
	  readHeader(pFI, pScanIndex[scanNum], &scanHeader);
	  if( scanHeader.msLevel == requestedMsLevel  && (scanHeader.peaksCount > 1) )
	    {
#ifdef DEBUG
	      cout << "Analyzing scan " << scanNum << endl;
#endif 
	      Mod.generateMic( scanNum );
	    }
	}
      
      if( !mass.empty() )
	{ // Know cross linker search
	  Mod.findCandidate( IO.getModifiedResidue() , IO.getNotTerminal() );
	}
      else
	{
	  if( IO.getFragmentType() == 'S' )
	    { // Simple search
	      Mod.findCandidate( IO.getModifiedResidue() , IO.getNotTerminal() );
	    }
	  else if( IO.getFragmentType() == 'X' )
	    { // Unknown cross linker search
	      cout << "Looking up crosslinked partners\n";
	      //Mod.findCandidates( IO.getModifiedResidue() , IO.getNotTerminal() );
	    }
	}

      vScan = Mod.getScanRes();
      Mod.resetVScan();
      cout << "I will remove " << IO.getPrecursorModificationMass() << " from the precursorMH mass\n";

	try
	{
	  Sa.setScanRes( vScan );
	}
	catch( exception &e )
	{
	  cerr << "Caught error: " << e.what() << endl;
	  exit(0);
	}

      Sa.setModificationMass( IO.getPrecursorModificationMass() );
      if( !mass.empty() )
	{ // Know cross linker search
	  Sa.scoreMod();
	  Sa.scoreCandidate();

	  if( doReverse )
	    {
	      Sa.addReverseData();
	      Sa.adjustScore();
	      Sa.calculateNumHigherScore( true );
	    }
          Sa.calculateRelativeScanPos();
	}
      else
	{
	  if( IO.getFragmentType() == 'S' )
	    { // Simple search
	      Sa.scoreCandidate();
	      Sa.scoreSimpleCandidate();
              Sa.calculateRelativeScanPos();
	    }
	  if( IO.getFragmentType() == 'X' )
	    { // Unknown cross linker search
	      //Sa.scoreSimpleCandidates();	// TODO PROGRAM THE REAL SCORING ROUTINE FOR XS !!!!
	    }
	}
      
      system( "mkdir plots" );

      if( IO.getNonInteractive() )
	{
	  Sa.prepareSumoXML();
	}
      else
	{
	  int choice;
	  bool firstNDone = false;
	  do
	    {
	      cout << endl
		   << "Please choose one of the following options:\n"
		   << "0. Quit\n"
		   << "1. Display scores\n"
		   << "2. Display scan number ...\n"
		   << "3. Display best scans\n"
		   << "4. Display next best scans\n"
		   << "5. Save results in XML file\n";
	      cin >> choice;

	      switch( choice )
		{
		case 0:
		  break;
		case 1:
		  Sa.printScore();
		  break;
		case 2:
		  Sa.plotScanNum();
		  break;
		case 3:
		  Sa.plotBestN();
		  firstNDone = true;
		  break;
		case 4:
		  if( firstNDone )
		    {
		      Sa.plotNextN();
		    }
		  else
		    {
		      Sa.plotBestN();
		      firstNDone = true;
		    }
		  break;
		case 5:
		  Sa.prepareSumoXML();
		}
	    }while( choice != 0 );
	}

      // We are done, let's clean up
      rampCloseFile(pFI);
    }

  delete pScanIndex;
  
  return 0;
}

```

---

### Post by SevenMachines on 2012-08-28
Your last error looks like the path to RAMP isnt set properly, heres a diff of my working Makefile
```
--- Makefile  2008-02-11 11:27:39.000000000 +0000
+++ /home/niall/Downloads/SUMmOn_2.0/SUMmOn/Makefile  2012-08-26 21:17:53.596834625 +0100
@@ -2,6 +2,7 @@
 CPPC=g++
 CC=gcc

+RAMPROOT=/home/niall/Downloads/TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp
 # Enable for profiling.
 #CCOPT=-pg

@@ -34,11 +35,11 @@

 OBJS = InOut.o quantitation.o PeaksUtils.o IonGenerator.o \
  Modifier.o SumoAnalysis.o Digestion.o Masses.o\
- ${RAMPROOT}/base64.o  ${RAMPROOT}/ramp.o main.o 
+ ${RAMPROOT}/ramp_base64.o ${RAMPROOT}/ramp.o main.o 

 OBJS_LNK = InOut.o quantitation.o PeaksUtils.o IonGenerator.o\
  Modifier.o SumoAnalysis.o Digestion.o Masses.o\
- base64.o ramp.o main.o
+ ramp_base64.o ramp.o main.o

 #
 # rules

```Have a try with that, making sure you've changed the RAMPROOT to your install location and post back whatever errors you get

---

### Post by nbhagwat on 2012-08-28
Thanks! That did solve a number of issues. Then it complained that ramp.cpp could nor find zlib.h. I found it in /usr/bin/syslinux/com32/include and pointed ramp.cpp to it. Now it's saying this:
```
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I/usr/local/src/ramp -I. -I/usr/include/gsl -Wno-deprecated -c ./ /usr/local/src/ramp/ramp_base64.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I/usr/local/src/ramp -I. -I/usr/include/gsl -Wno-deprecated -c ./ /usr/local/src/ramp/ramp.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I/usr/local/src/ramp -I. -I/usr/include/gsl -Wno-deprecated -c ./ main.cpp
main.cpp: In function ‘int main(int, char**)’:
main.cpp:147:35: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
main.cpp:150:144: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
main.cpp:161:143: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
g++: warning: ./: linker input file unused because linking not done
g++   -o summon InOut.o quantitation.o PeaksUtils.o IonGenerator.o Modifier.o SumoAnalysis.o Digestion.o Masses.o ramp_base64.o ramp.o main.o -L/usr/lib -L/usr/include/gsl/.libs -L/usr/include/gsl/cblas/.libs -lgsl -lgslcblas -lz -lm
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
make: *** [main] Error 1

```

Many thanks for your help.

---

### Post by SevenMachines on 2012-08-29
I'll put together a howto later, thats probably simpler, see how you get on with that

---

### Post by SevenMachines on 2012-08-29
This works for building Summon on 64bit Ubuntu 12.04

* Download Summon [http://sourceforge.net/projects/summon/files/latest/download?source=files](http://sourceforge.net/projects/summon/files/latest/download?source=files)
* Download Ramp (in TPP) [http://sourceforge.net/projects/sashimi/files/latest/download?source=files](http://sourceforge.net/projects/sashimi/files/latest/download?source=files)

Then
```
$ tar -zvxf SUMmOn_2.0.tgz 
$ tar -zvxf TPP-4.6-src.tgz
# and get to our summon build dir
$ cd SUMmOn_2.0/SUMmOn
```

Attempting to build on newer gcc chain will lead to a lot of these....
error: 'strcpy' was not declared in this scope
error: 'strlen' was not declared in this scope
Meaning #include <ctring> is missing

error: 'exit' was not declared in this scope
Meaning #include <cstlib> is missing

error: 'sort' was not declared in this scope
error: 'reverse' was not declared in this scope
Meaning #include <algorithm> is missing

So we need to patch the includes in

includes-diff:
```
diff -ruN SUMmOn.orig/Digestion.hpp SUMmOn.build/Digestion.hpp
--- SUMmOn.orig/Digestion.hpp 2012-08-29 22:14:14.940239387 +0100
+++ SUMmOn.build/Digestion.hpp  2012-08-29 22:24:50.368265731 +0100
@@ -31,6 +31,8 @@
 #include <iostream>
 #include <vector>
 #include <string>
+#include <cstdlib>
+#include <algorithm>
 #include "AminoAcidMasses.hpp"

 using namespace std;
diff -ruN SUMmOn.orig/InOut.hpp SUMmOn.build/InOut.hpp
--- SUMmOn.orig/InOut.hpp 2012-08-29 22:14:14.936239388 +0100
+++ SUMmOn.build/InOut.hpp  2012-08-29 22:20:03.284253829 +0100
@@ -34,6 +34,9 @@

 #include "gsl/gsl_histogram.h"

+#include <cstring>
+#include <algorithm>
+
 using namespace std;

 class InOut
diff -ruN SUMmOn.orig/IonGenerator.hpp SUMmOn.build/IonGenerator.hpp
--- SUMmOn.orig/IonGenerator.hpp  2012-08-29 22:14:14.936239388 +0100
+++ SUMmOn.build/IonGenerator.hpp 2012-08-29 22:23:48.976263185 +0100
@@ -30,6 +30,9 @@

 #include <iostream>
 #include <vector>
+#include <cstring>
+#include <cstdlib>
+#include <algorithm>

 using namespace std;

diff -ruN SUMmOn.orig/libraResults.hpp SUMmOn.build/libraResults.hpp
--- SUMmOn.orig/libraResults.hpp  2012-08-29 22:14:14.936239388 +0100
+++ SUMmOn.build/libraResults.hpp 2012-08-29 22:20:03.284253829 +0100
@@ -33,6 +33,9 @@
 #include <fstream>
 #include <assert.h>

+#include <cstring>
+#include <cstdlib>
+
 using namespace std;

 class intensityAnalysis


```
$ patch -p1 <includes-diff 
patching file Digestion.hpp
patching file InOut.hpp
patching file IonGenerator.hpp
patching file libraResults.hpp


# Now we need to find ramp
```
$ find  ../../TPP-4.6/ -name 'ramp'            
../../TPP-4.6/trans_proteomic_pipeline/extern/ProteoWizard/pwiz/pwiz/data/msdata/ramp
../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp

```
# So edit the Make file and add
```
RAMPROOT=../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp

```

# Now we have this problem 
```
make: *** No rule to make target `../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp/base64.o', needed by `main'.  Stop.
```

# On a guess, this file has been renamed ramp_base64 so rename in the Makefile
```
$ grep base64 *
Makefile:	${RAMPROOT}/base64.o	${RAMPROOT}/ramp.o main.o 
Makefile:	base64.o ramp.o main.o
Makefile:base64.o: ${RAMPROOT}/base64.c ${RAMPROOT}/base64.h

$ sed -i 's/base64.h/ramp_base64.h/g' Makefile 
$ sed -i 's/base64.c/ramp_base64.c/g' Makefile 
$ sed -i 's/base64.o/ramp_base64.o/g' Makefile 
```

# Or try the diff
```
--- SUMmOn.orig/Makefile  2012-08-29 22:14:14.940239387 +0100
+++ SUMmOn/Makefile 2012-08-29 22:29:31.252277375 +0100
@@ -4,6 +4,7 @@

 # Enable for profiling.
 #CCOPT=-pg
+RAMPROOT=../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp

 # put here the complete path to the RAMP include directory
 RAMPINC= -I. -I${RAMPROOT}
@@ -34,11 +35,11 @@

 OBJS = InOut.o quantitation.o PeaksUtils.o IonGenerator.o \
  Modifier.o SumoAnalysis.o Digestion.o Masses.o\
- ${RAMPROOT}/base64.o  ${RAMPROOT}/ramp.o main.o 
+ ${RAMPROOT}/ramp_base64.o ${RAMPROOT}/ramp.o main.o 

 OBJS_LNK = InOut.o quantitation.o PeaksUtils.o IonGenerator.o\
  Modifier.o SumoAnalysis.o Digestion.o Masses.o\
- base64.o ramp.o main.o
+ ramp_base64.o ramp.o main.o

 #
 # rules
@@ -82,6 +83,6 @@
 Modifier.o: Modifier.cpp Modifier.hpp
 SumoAnalysis.o: SumoAnalysis.cpp SumoAnalysis.hpp
 Digestion.o: Digestion.cpp Digestion.hpp
-base64.o: ${RAMPROOT}/base64.c ${RAMPROOT}/base64.h
+ramp_base64.o: ${RAMPROOT}/ramp_base64.c ${RAMPROOT}/ramp_base64.h
 ramp.o : ${RAMPROOT}/ramp.c  ${RAMPROOT}/ramp.h
 main.o: main.cpp

```
```
$ patch -p1 <makefile-diff 
patching file Makefile
```

Now
```
$ make 

```
# Success???
```
$ ./summon --help
Usage SUMmOn -c <condition file> <input file name>

```

---

### Post by nbhagwat on 2012-08-29
THANKS!!!
If this works, you can have my first-born.

P.S. you'll have to wait for a while

---

### Post by nbhagwat on 2012-08-30
Nope!
I am getting the same set of errors as I was getting before. First I get:
```
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ InOut.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ quantitation.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ PeaksUtils.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ IonGenerator.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ Modifier.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ SumoAnalysis.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ Digestion.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ Masses.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ ../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp/ramp_base64.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ ../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp/ramp.cpp
../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp/ramp.cpp:1589:18: fatal error: zlib.h: No such file or directory
compilation terminated.
make: *** [../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp/ramp.o] Error 1

```

Then, after I fix that:
```
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ ../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp/ramp_base64.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ ../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp/ramp.cpp
g++: warning: ./: linker input file unused because linking not done
g++ -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE     -I. -I../../TPP-4.6/trans_proteomic_pipeline/src/Parsers/ramp -I. -I -Wno-deprecated -c ./ main.cpp
main.cpp: In function ‘int main(int, char**)’:
main.cpp:147:35: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
main.cpp:150:144: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
main.cpp:161:143: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
g++: warning: ./: linker input file unused because linking not done
g++   -o summon InOut.o quantitation.o PeaksUtils.o IonGenerator.o Modifier.o SumoAnalysis.o Digestion.o Masses.o ramp_base64.o ramp.o main.o -L/usr/lib -L/.libs -L/cblas/.libs -lgsl -lgslcblas -lz -lm
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
make: *** [main] Error 1

```

Any idea what's missing here?

---

### Post by SevenMachines on 2012-08-30
You're missing a dependency, apt-file search <something.h> is often good for these, in this case its

```
$ sudo apt-get install zlib1g-dev
```

---

### Post by nbhagwat on 2012-08-30
That did it!
Thanks!

---

