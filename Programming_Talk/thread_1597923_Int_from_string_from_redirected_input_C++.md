---
title: "Int from string from redirected input C++"
date: 2010-10-15
forum: Programming Talk
---

### Post by PirateMcplunder on 2010-10-15
Hello!

I am working on some code which is eventually supposed to simulate (very primitively) packed fragmentation and reassembly in a transparent network. Unfortunately, I can't seem to read in the input correctly.

The puzzling thing to me is that I have some code where I seem to be able to read in the first integer on the first line correctly (num_hops) but I can't read in subsequent integers with essentially the same code!!

Any help, suggestions, tips, pointers or hints would be greatly appreciated.

An example of the input is as follows:
[INDENT]2	#number of hops
35 # maximum payload size for hop 1
20 # maximum payload size for hop 2
27 0 0 "This is the payload, whi"
27 24 0 "ch may span multiple lin"
27 48 1 "es until end of input."[/INDENT]

As you can see, the pound signs are convenient delimiters.  I am trying to use getline to grab each line of input (all of which is redirected from a file as standard input) and then I am trying to use getline again with a delimiter to chop the line up.  Finally, I am trying to use streams to get the first part of the string (which should just be an int) into a variable of type int.

Why does this work the first time and not subsequently?

```
#include <iostream>
#include <sstream>
#include <string>
#include <stdio.h>
using namespace std;

int main () {

	int num_hops;					/* number of hops within hypothetical network */
	string first_input_line;		
	string* max_payload_lines;		/* placeholder for array of strings, containing input lines with maximum payload values.  The count of these lines should be = to the number of hops */
	int* max_payloads;				/* placeholder for array of integers, containing the maximum payload values themselves.  The count of these values should be = to the number of hops */
	string* restof_input_lines;		/* string array for the remaining lines of input (i.e. packet/payload lines) */
	string before_token;			/* buffer for string before delimiting token */
	string after_token;				/* buffer for string after delimiting token */
	stringstream input_buffer;			/* stringstream for reading input from stdin */
	stringstream conversion_buffer;		/* stringstream for variable assignment */
	size_t found;					/* flag for checking references to appropriate fields when input lines are scanned for expected descriptors in their comments */

	/* Usage */
	string usage = "Usage:\np2 < testfile\n\nWhere testfile is the name of a field containing input data in the following format\n2	#number of hops\n35 # maximum payload size for hop 1\n20 # maximum payload size for hop 2\n27 0 0 \"This is the payload, whi\"\n27 24 0 \"ch may span multiple lin\"\n27 48 1 \"es until end of input.\"";

	/* interpret initial input */

		/* get first line */
		if(!getline(cin, first_input_line)){
		cerr << "Getline failure. Are you sure you redirected input?!" << endl;
		cerr << usage << endl;
		}

		input_buffer << first_input_line;

		found=first_input_line.find("number of hops");		/* check first line for reference to the number of hops. */
		if (found==string::npos){
		cerr << "No explicit reference to \"number of hops\" found in the comment for first input line." << endl;
		cerr << usage << endl;
		exit(1);
		}	
		
		getline(input_buffer, before_token, '#');	/* get first input line up to token "#", set value for num_hops */
		cout << before_token << endl;
		conversion_buffer << before_token;
		conversion_buffer >> num_hops;

		/* clear values of buffers, string placeholders and flags for future reuse */
		found = 0;
		input_buffer.clear(stringstream::goodbit);
		conversion_buffer.clear(stringstream::goodbit);
		before_token = "";
		after_token = "";
		/* now we know the number of hops and therefore the number of maximum payload lines to expect */

	/* get lines containing maximum payloads for each hop */
	max_payloads = new int[num_hops];				/* initialize and zero array of ints for stroing maximum payload values to the size of the number of hops */
		for (int i = 0 ; i < num_hops ; i ++){
			max_payloads[i] = 0;
		}

	max_payload_lines = new string[num_hops];  		/* initialize array of strings for stroing maximum payload line comments to the size of the number of hops */
	
	for(int j = 0 ; j < num_hops ; j++){
		if(!getline(cin, max_payload_lines[j])){
		cerr << "Getline failure. Are you sure you redirected input correctly?!" << endl;
		cerr << usage << endl;
		exit(2);
		}

		input_buffer << max_payload_lines[j];	

		found=max_payload_lines[j].find("maximum payload size");	/* search line for comment pertaining to maximum payload size */
		if (found==string::npos){
		cerr << "No explicit reference to \"maximum payload size\" found in the comment for input line #" << j << "\nAre you sure that you entered input correctly?" << endl;
		cerr << usage << endl;
		exit(3);
		}	

		getline(input_buffer, before_token, '#');	/* get next input line pertaining to maximum payload size up to token "#", set value for num_hops */
		cout << before_token << endl;
		conversion_buffer << before_token;
		conversion_buffer >> max_payloads[j];	/* set maxmimum payload for this hop */

		/* clear values of buffers, string placeholders and flags for future reuse */
		found = 0;
		input_buffer.clear(stringstream::goodbit);
		conversion_buffer.clear(stringstream::goodbit);
		before_token = "";
		after_token = "";
	}

	cout << num_hops << endl;
	for (int k = 0 ; k < num_hops ; k++)
	{
		cout << max_payloads[k] << endl;
		cout << max_payload_lines[k] << endl;
	}

		/* now we have the number of hops and the maximum payload for each hop.  it's time to read in the input packets! */
}

```

Thank you for your time and for your help!

---

### Post by PirateMcplunder on 2010-10-15
I've been looking for hours and I think I've identified the problem as having to do with the state of the stringstream (which would explain the working once and then breaking problem).  I am using .clear after each use of the stringstreams, however; shouldn't this reset their state?

---

### Post by PirateMcplunder on 2010-10-15
Current output is:
2
number of hops35
 maximum payload size for hop 120
2
0
35 # maximum payload size for hop 1
0
20 # maximum payload size for hop 2

where:
the first 2 is the "before_token" string after the streams are used successfully the first time
and the second and third lines are the "before_token" string printed just after the second attempt at a similar process.

---

### Post by PirateMcplunder on 2010-10-15
The only answers I've been able to find for problems similar to my own is to clear the state of the streams with .clear, but I am doing this already...

see: [http://www.velocityreviews.com/forums/t283927-istringstream-str-only-works-once.html]("http://www.velocityreviews.com/forums/t283927-istringstream-str-only-works-once.html")

---

### Post by PirateMcplunder on 2010-10-15
SOLVED:

DUUUURRRRRRRRRRRRRRR.

I was reseting the state of the stream but not the values in the stream itself!

"input_buffer.clear();"
was not enough.

**input_buffer.str("");**
was needed.

another lesson learned (beyond this technical one about streams) is to be very liberal with the print statements when debugging.  If I remember that, maybe I'll save myself some time next time!

hope this helps someone else out in the future.

---

