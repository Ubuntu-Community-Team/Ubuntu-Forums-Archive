---
title: "separating channel data using libsndfile"
date: 2009-11-20
forum: Programming Talk
---

### Post by debugdom on 2009-11-20
Hello-

I'm new to c+ (this is the first thing i've done) and I've managed to piece together how to open a wave file using libsndfile and pull its data into an array, however I'm not sure if i'm pulling the left channel or the right channel or a combination of the two, the libsndfile mailing list seems to be dead otherwise I would have begged for help on there.

what channel of data am i putting into the rawWaveDataArray?

any help would be great

thanks!

heres the code:

```
int ReadWave::waveFileToArray(){
	
	//sndfile obj + soundfile info object
	SNDFILE *sf;
	
   SF_INFO info;
	
   int num;
	int num_items;

	int numFrames;
	int sampleRate;
	int channels;

	int i;
	int j;
	
   FILE *out;
	
	
	SNDFILE *outWave;
	// open the wave

	info.format = 0;
   sf = sf_open(filePath, SFM_READ,&info);
   if (sf == NULL)
       {
       printf("Failed to open the file.\n");
       exit(-1);
	}
	
	numFrames = info.frames;
   sampleRate = info.samplerate;
   channels = info.channels;
	
	num_items = numFrames * channels;


	vector <int> buffer(num_items);

	num = sf_read_int(sf, &buffer[0], num_items);
	sf_close(sf);



	
	for (i = 0; i < num; i += channels){
     	
			rawWaveDataArray.push_back(buffer[i]);
			

	}

	
	printf("the array size is: %d \n", rawWaveDataArray.size());
	
   printf("frames=%d\n", numFrames);
   printf("samplerate=%d\n", sampleRate);
   printf("channels=%d\n",channels);

   printf("num_items=%d\n",num_items);
	printf("Read %d items\n", num);
	
	for(i = 0; i < rawWaveDataArray.size(); i++){
		printf("%d\n", rawWaveDataArray[i]);
	}

   fclose(out);

	return 0;
}
```

---

