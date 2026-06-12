---
title: "error message compiling C# in xcode with defined functions"
date: 2008-12-06
forum: Programming Talk
---

### Post by themusicalduck on 2008-12-06
Hey,

I'm trying to compile a C# program that will link up to a max/msp patch working as sequencer and drum machine.

This is the code I'm trying to compile:

```
#include "aservelib.h"
#include <stdio.h>
#include "math.h"
#include <unistd.h>

void drums(void);
void synthesiser(void);

int main ()
{	
	int note;
	float frequency;
	float playfrequency;
	int sampleno;
	
	
	//void AserveSample(int sampleNumber, float amplitude);
	while(true)
	{
		note = AserveGetNote();
		frequency = 440.0 * pow(2.0, (note - 69.0) / 12.0);
	
		while(true)
		{
			int channel;
			channel = AserveGetNoteChannel();
			
			if (channel = 10)
			{				
				drums();				
			}
			else if (channel = 1)
			{				
				synthesiser();
			}
				
		return 0;
	}
		}
	
		
	void drums(void);		
		{
			
		switch(note)
		
		{

			case 10:
				sampleno = 0;
				break;
			case 11:
				sampleno = 1;
				break;
			case 12:
				sampleno = 2;
				break;
			case 13:
				sampleno = 3;
				break;
			case 14:
				sampleno = 4;
				break;
			case 15:
				sampleno = 5;
				break;
			case 16:
				sampleno = 6;
				break;
			case 17:
				sampleno = 7;
				break;
				
				
			default:
				printf("invalid Number");
				break;
		}	
	
		AserveSample(sampleno, 1.0);
		}
		
	void synthesiser(void);
		
		{
		
		switch(note)
		{
				
			case 60:
			playfrequency = frequency;
			break;
			
			case 61:
				frequency = playfrequency;
				break;
				
			case 62:
				frequency = playfrequency;
				break;

			case 63:
				frequency = playfrequency;
				break;
				
			case 64:
				frequency = playfrequency;
				break;

			case 65:
				frequency = playfrequency;
				break;

			case 66:
				frequency = playfrequency;
				break;

			case 67:
				frequency = playfrequency;
				break;

			case 68:
				frequency = playfrequency;
				break;

			case 69:
				frequency = playfrequency;
				break;

			case 70:
				frequency = playfrequency;
				break;

			case 71:
				frequency = playfrequency;
				break;

			case 72:
				frequency = playfrequency;
				break;
				
			default:
				printf("invalid Number");
				break;
				
		}
		
		AserveOscillator(0, playfrequency, 1.0, 0);
		
		}
}
```

The error message I get is:

Linking /network/path/
"drums()", referenced from:
_main in main.o
symbol(s) not found
collect2: Id returned 1 exit status
Build failed (2 errors)

I am using xcode and can't work it out!

---

### Post by themusicalduck on 2008-12-06
bump

---

### Post by cszikszoy on 2008-12-07
This is C code... not C# code.

---

### Post by themusicalduck on 2008-12-07
Whoops, my bad. Can you tell I've only been doing this a few weeks?

Does anyone have a reply as to what the error might be about?

---

### Post by wmcbrine on 2008-12-08
1. Your brackets are all screwed up. It kinda looks like you're trying to create drums() and synthesizer() as functions within the main() function. C doesn't support nested functions. Make them all top-level.

2. Remove the semicolon after the second "void drums(void)", and the second "void synthesizer(void)". A semicolon says "this is the end", which is what you want for the prototypes (at the top), but not for the actual function definitions.

---

