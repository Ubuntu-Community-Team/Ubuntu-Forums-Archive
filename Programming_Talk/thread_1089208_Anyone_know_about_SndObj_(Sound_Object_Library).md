---
title: "Anyone know about SndObj (Sound Object Library)"
date: 2009-03-06
forum: Programming Talk
---

### Post by gafferuk on 2009-03-06
Im trying to get a simple example working using SndObj library, just a case of reading a wave file and sending it out to the soundcard, but all im receiving is a static type sound. anyone got any ideas?

thanks,
Paul

```
#define ALSA 1

#include <SndObj/AudioDefs.h>

#include <string.h>

#include <math.h>

#include <time.h>

#ifndef WIN32

#include <unistd.h>

#endif

 

int

main(int argc, char** argv){

	 time_t ts, te;

	char* infile = argv[1];



         time(&ts);



	// input sound

	SndRead input(infile,1.0f, 1.0f,DEF_VECSIZE, DEF_SR);

	SndObj*  left_channel = input.Outchannel(1);

	SndObj*  right_channel = input.Outchannel(2);



	SndRTIO output(2, SND_OUTPUT,512,

       12,SHORTSAM_LE, 0,

         DEF_VECSIZE,DEF_SR,"hw:1");

         

	output.SetOutput(1, left_channel);

	output.SetOutput(2, right_channel);

	

	// processing loop

	while(true){

          input.DoProcess();

          left_channel->DoProcess();

          right_channel->DoProcess();         

          

         output.Write();

	}

  

	time(&te);	cout << " process time (secs): " << (te -ts) << "\n";

	return 0;

}
```

---

