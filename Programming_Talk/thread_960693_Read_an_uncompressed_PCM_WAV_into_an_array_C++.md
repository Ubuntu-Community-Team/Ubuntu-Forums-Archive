---
title: "Read an uncompressed PCM WAV into an array C++"
date: 2008-10-27
forum: Programming Talk
---

### Post by tom66 on 2008-10-27
I would like to be able to open a WAV file, then read each of the values in it into an array of appropriate size (I should be able to find out the size from the WAV, if possible, then allocate an array of integers using malloc/new.) I am doing this for a personal project. Would be best in a library or using a toolkit of some kind.

Thanks,
Tom

---

### Post by tCarls on 2008-10-27
Here's a good specification of the WAV format:
[http://ccrma.stanford.edu/courses/422/projects/WaveFormat/](http://ccrma.stanford.edu/courses/422/projects/WaveFormat/)

I don't know of any libraries but it's easy enough to parse a WAV file in C. This is how I do it: (note: it's c++ and I use a couple classes that I don't define here, but hopefully it's clear enough. Let me know if you have any questions.)

Basically, first you read the header to determine the number of channels, sample rate, bits per sample, and number of samples; then you use that information to malloc your data; then you read the rest of the file and store it in your data.

```

void Read_wav::read_wav(const string &filename, int ***data,
                unsigned int **data_size, wav_params **params)
{
        c_file_handle file(filename, "r");
        unsigned int num_ch, samp_rate, bits_per_samp, num_samp;
        read_wav_header(file, &num_ch, &samp_rate, &bits_per_samp, &num_samp);

        *params = new wav_params(num_ch, samp_rate, bits_per_samp);
        *data = (int **) calloc(num_ch, sizeof(int *));
        assert(*data);
        *data_size = (unsigned int *) malloc(num_ch * sizeof(unsigned int));
        assert(*data_size);
        for (unsigned int i=0; i < num_ch; ++i) {
                *data[i] = (int *) malloc(num_samp * sizeof(int));
                *data_size[i] = num_samp;
        }

        read_wav_data(file, *data, **params, num_samp);
}


inline void Read_wav_impl::read_wav_header(c_file_handle &file,
                unsigned int *num_ch, unsigned int *samp_rate,
                unsigned int *bits_per_samp, unsigned int *num_samp)
{
        unsigned char buffer[5];

        /* ChunkID (RIFF for little-endian, RIFX for big-endian) */
        file.read(buffer, 4);
        buffer[4] = '\0';
        if (strcmp((char*)buffer, "RIFF")) {
                throw except("RIFF file format not detected", file.filename);
        }

        /* ChunkSize */
        file.read(buffer, 4);
        /* UNUSED
        const unsigned int chunk_size = buffer[0] + (buffer[1] << 8) +
                (buffer[2] << 16) + (buffer[3] << 24);
        */

        /* Format */
        file.read(buffer, 4);
        buffer[4] = '\0';
        if (strcmp((char*)buffer, "WAVE")) {
                throw except("WAVE file format not detected", file.filename);
        }

        /* Subchunk1ID */
        file.read(buffer, 4);
        buffer[4] = '\0';
        if (strcmp((char*)buffer, "fmt ")) {
                throw except("fmt section not found", file.filename);
        }

        /* Subchunk1Size (16 for PCM) */
        file.read(buffer, 4);
        if (buffer[0] != 16 || buffer[1] || buffer[2] || buffer[3]) {
                throw except("PCM format not detected", file.filename);
        }

        /* AudioFormat (PCM = 1, other values indicate compression) */
        file.read(buffer, 2);
        if (buffer[0] != 1 || buffer[1]) {
                throw except("PCM format not detected", file.filename);
        }

        /* NumChannels (Mono = 1, Stereo = 2, etc) */
        file.read(buffer, 2);
        *num_ch = buffer[0] + (buffer[1] << 8);

        /* SampleRate (8000, 44100, etc) */
        file.read(buffer, 4);
        *samp_rate = buffer[0] + (buffer[1] << 8) +
                (buffer[2] << 16) + (buffer[3] << 24);

        /* ByteRate (SampleRate * NumChannels * BitsPerSample / 8) */
        file.read(buffer, 4);
        const unsigned int byte_rate = buffer[0] + (buffer[1] << 8) +
                (buffer[2] << 16) + (buffer[3] << 24);

        /* BlockAlign (NumChannels * BitsPerSample / 8) */
        file.read(buffer, 2);
        const unsigned int block_align = buffer[0] + (buffer[1] << 8);

        /* BitsPerSample */
        file.read(buffer, 2);
        *bits_per_samp = buffer[0] + (buffer[1] << 8);

        if (byte_rate != ((*samp_rate * *num_ch * *bits_per_samp) >> 3)) {
                throw except("ByteRate != SampleRate * NumChannels * "
                                "BitsPerSample / 8", file.filename);
        }

        if (block_align != ((*num_ch * *bits_per_samp) >> 3)) {
                throw except("BlockAlign != NumChannels * "
                                "BitsPerSample / 8", file.filename);
        }

        /* Subchunk2ID */
        file.read(buffer, 4);
        buffer[4] = '\0';
        if (strcmp((char*)buffer, "data")) {
                throw except("data section not found", file.filename);
        }

        /* Subchunk2Size (NumSamples * NumChannels * BitsPerSample / 8) */
        file.read(buffer, 4);
        const unsigned int subchunk2_size = buffer[0] + (buffer[1] << 8) +
                (buffer[2] << 16) + (buffer[3] << 24);
        *num_samp = (subchunk2_size << 3) / (
                        *num_ch * *bits_per_samp);
}


inline void Read_wav_impl::read_wav_data(c_file_handle &file, int **data,
                const wav_params &params, unsigned int num_samp)
{
        const unsigned int num_ch = params.num_ch;
        const unsigned int bits_per_samp = params.bits_per_samp;
        unsigned char buffer;
        for (unsigned int i=0; i != num_samp; ++i) {
                for (unsigned int j=0; j != num_ch; ++j) {
                        unsigned int tmp = 0;
                        for (unsigned int k=0; k != bits_per_samp; k+=8) {
                                file.read(&buffer, 1);
                                tmp += buffer << k;
                        }
                        data[j][i] = conv_bit_size(tmp, bits_per_samp);
                }
        }
}


inline int Read_wav_impl::conv_bit_size(unsigned int in, int bps)
{
        const unsigned int max = (1 << (bps-1)) - 1;
        return in > max ? in - (max<<1) : in;
}

```

---

### Post by tom66 on 2008-10-27
Thanks, I'll check that out.

I have a question: If I have a binary integer stored in a file - let's say it's 4 bytes long, how do I read that in as a normal integer? Do I just copy it into memory? What if it is the other way around (little/big endian)? 

Thanks.

Also, what does a triple pointer do? (int ***)

---

### Post by tCarls on 2008-10-27
> 
I have a question: If I have a binary integer stored in a file - let's say it's 4 bytes long, how do I read that in as a normal integer? Do I just copy it into memory? What if it is the other way around (little/big endian)?


If it's little endian and four bytes then you can read directly into the integer:

```

unsigned int little_endian_value;
fread(&little_endian_value, 4, 1, fp);

```

However, I get confused easily with endianness and like to be safe by always reading one byte at a time and combining the bytes with bit shifts and either addition or binary-or's:

```

char buf[4];
unsigned int little_endian_value, big_endian_value;
fread(buf, 1, 4, fp);
little_endian_value = buf[0] | (buf[1] << 8) | (buf[2] << 16) | (buf[3] << 24);
big_endian_value = (buf[0] << 24) | (buf[1] << 16) | (buf[2] << 8) | buf[3];

```

---

### Post by tCarls on 2008-10-27
> 
Also, what does a triple pointer do? (int ***) 


The int ***data? data is a pointer to an array of arrays. *data is an array of arrays (one for each audio channel.) **data is an array (the raw data for that particular channel.)

(*data)[0] would be the array of raw data for the left channel.
(*data)[1] would be the array of raw data for the right channel.
(*data)[0][0] would be the first sample of the left channel.

I know it kind of seems like overkill. The pointer needs to be passed to the function so the array of arrays can be malloc'd.

---

### Post by tom66 on 2008-10-27
I think it would be easy if, for my required usage, take a simple average of the two channels.

---

### Post by tCarls on 2008-10-27
Okay, here's 124 lines of plain C, complete enough to compile. It assumes a mono wav file. If anything goes wrong it exits without printing an error. It reads from stdin. The wav data ends up in the "data" array in the main() function. I don't guarantee it's correct, but it should give you a good start. Good luck.

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void read_wav_header(unsigned int *samp_rate, unsigned int *bits_per_samp,
		unsigned int *num_samp);
void read_wav_data(int *data, unsigned int samp_rate,
		unsigned int bits_per_samp, unsigned int num_samp);
int conv_bit_size(unsigned int in, int bps);

int main(void)
{
        unsigned int samp_rate, bits_per_samp, num_samp;
        read_wav_header(&samp_rate, &bits_per_samp, &num_samp);
	printf("samp_rate=[%d] bits_per_samp=[%d] num_samp=[%d]\n",
		samp_rate, bits_per_samp, num_samp);

	int *data = (int *) malloc(num_samp * sizeof(int));
        read_wav_data(data, samp_rate, bits_per_samp, num_samp);

	unsigned int i;
	for (i = 0; i < num_samp; ++i) {
		printf("%d\n", data[i]);
	}

	return EXIT_SUCCESS;
}

void read_wav_header(unsigned int *samp_rate, unsigned int *bits_per_samp,
		unsigned int *num_samp)
{
        unsigned char buf[5];

        /* ChunkID (RIFF for little-endian, RIFX for big-endian) */
        fread(buf, 1, 4, stdin);
        buf[4] = '\0';
        if (strcmp((char*)buf, "RIFF")) exit(EXIT_FAILURE);

        /* ChunkSize */
        fread(buf, 1, 4, stdin);

        /* Format */
        fread(buf, 1, 4, stdin);
        buf[4] = '\0';
        if (strcmp((char*)buf, "WAVE")) exit(EXIT_FAILURE);

        /* Subchunk1ID */
        fread(buf, 1, 4, stdin);
        buf[4] = '\0';
        if (strcmp((char*)buf, "fmt ")) exit(EXIT_FAILURE);

        /* Subchunk1Size (16 for PCM) */
        fread(buf, 1, 4, stdin);
        if (buf[0] != 16 || buf[1] || buf[2] || buf[3]) exit(EXIT_FAILURE);

        /* AudioFormat (PCM = 1, other values indicate compression) */
        fread(buf, 1, 2, stdin);
        if (buf[0] != 1 || buf[1]) exit(EXIT_FAILURE);

        /* NumChannels (Mono = 1, Stereo = 2, etc) */
        fread(buf, 1, 2, stdin);
        unsigned int num_ch = buf[0] + (buf[1] << 8);
	if (num_ch != 1) exit(EXIT_FAILURE);

        /* SampleRate (8000, 44100, etc) */
        fread(buf, 1, 4, stdin);
        *samp_rate = buf[0] + (buf[1] << 8) +
                (buf[2] << 16) + (buf[3] << 24);

        /* ByteRate (SampleRate * NumChannels * BitsPerSample / 8) */
        fread(buf, 1, 4, stdin);
        const unsigned int byte_rate = buf[0] + (buf[1] << 8) +
                (buf[2] << 16) + (buf[3] << 24);

        /* BlockAlign (NumChannels * BitsPerSample / 8) */
        fread(buf, 1, 2, stdin);
        const unsigned int block_align = buf[0] + (buf[1] << 8);

        /* BitsPerSample */
        fread(buf, 1, 2, stdin);
        *bits_per_samp = buf[0] + (buf[1] << 8);

        if (byte_rate != ((*samp_rate * num_ch * *bits_per_samp) >> 3))
		exit(EXIT_FAILURE);

        if (block_align != ((num_ch * *bits_per_samp) >> 3))
		exit(EXIT_FAILURE);

        /* Subchunk2ID */
        fread(buf, 1, 4, stdin);
        buf[4] = '\0';
        if (strcmp((char*)buf, "data")) exit(EXIT_FAILURE);

        /* Subchunk2Size (NumSamples * NumChannels * BitsPerSample / 8) */
        fread(buf, 1, 4, stdin);
        const unsigned int subchunk2_size = buf[0] + (buf[1] << 8) +
                (buf[2] << 16) + (buf[3] << 24);
        *num_samp = (subchunk2_size << 3) / (
                        num_ch * *bits_per_samp);
}


void read_wav_data(int *data, unsigned int samp_rate,
		unsigned int bits_per_samp, unsigned int num_samp)
{
        unsigned char buf;
	unsigned int i, j;
        for (i=0; i < num_samp; ++i) {
		unsigned int tmp = 0;
		for (j=0; j != bits_per_samp; j+=8) {
			fread(&buf, 1, 1, stdin);
			tmp += buf << j;
		}
		data[i] = conv_bit_size(tmp, bits_per_samp);
        }
}


int conv_bit_size(unsigned int in, int bps)
{
        const unsigned int max = (1 << (bps-1)) - 1;
        return in > max ? in - (max<<1) : in;
}


```

---

### Post by Eternal-student on 2009-04-11
I know this is an old thread but I found the information here so useful!  However, there is a small error in the calculation when converting the bit size.. 

The format for 16-bit wav the values

0x0000 = 0
0x7FFF = 32767
0x8000 = -32768
0xFFFF = -1

The format for 8-bit wav is slightly different as the values are all unsigned (not sure about this though). I think they only range from 0 - 32767

So the conv_bit_size function should return this value..

```
return in > max ? in - ((max<<1)**+2**) : in;
```

For example if you've got a 4 bit word the max value

```
const unsigned int max = (1 << (bps-1)) - 1;  // in binary 1000 - 1 = 0111
```

as max<<1 = 1110 = 14

---

### Post by EricBrotto on 2011-02-09
I also think this post is absolutely amazing. The information is super helpful to a project that I'm working on. 

The code that is written in C seems great. One question though:

Where do you place the URL for the file name and location?

Thanks!

---

### Post by tCarls on 2011-02-09
Do you mean the file name and location of the WAV file? In the C code I set it to read from standard in, so if your file is /home/eric/example.wav and the executable is named a.out then you would run:
```
./a.out < /home/eric/example.wav
```

The original code I posted in C++ didn't hardcode the file to stdin. I used some classes I didn't define so maybe some things weren't clear, but take a look at how the "file" variable is used and you can see what you need to do if you want to read from somewhere other than stdin. My c_file_handle class is below in case it helps make the code clearer; it's basically a FILE*.

```

class c_file_handle
{
public:
        inline c_file_handle(const std::string &name, const std::string &mode)
                        : filename(name) {
                file = fopen(name.c_str(), mode.c_str());
                if (!file) {
                        throw except("could not open " + name +
                                        ": " + strerror(errno), name);
                }
        }
        inline ~c_file_handle(void) { if (file) fclose(file); }
        inline void read(unsigned char *ptr, size_t nmemb) {
                if (fread(ptr, sizeof(unsigned char), nmemb, file) != nmemb) {
                        throw except("unexpected EOF", filename);
                }
        }
        const std::string filename;
        FILE *file;
};

```

---

### Post by josh. on 2011-06-04
This thread has been very useful to me! However i have run into a big problems where my read data function is only reading in about 1000 samples when there are about 13 million samples in the wav file i am processing! The FILE* seems to set the eof flag after this many samples and i have no idea why! Do you have any suggestions as to what might be causing this issue!!
I have tried testing the length of the file and found it contains 26 million bytes as expected, but when i read the data in it just stops working :S I also tried reading all the data block in with one call of:
```
fread(&buf,1,subchunk2Size,AudioFile);
```
where AudioFile is my file pointer. However all the samples after the first 1000 or so are all set to -1 :S Any suggestions?

EDIT:
I believe i have solved my own problem. If anyone has the same issue, by changing the file to open in binary mode
```
AudioFile = fopen(filepath,"rb");
```
not
```
AudioFile = fopen(filepath,"r");
```
I seem to be able to read the file in correctly :D

---

