---
title: "Segmentation fault"
date: 2016-04-23
forum: Programming Talk
---

### Post by kryptophonia on 2016-04-23
I've been writing this program for over half a year now and I cannot find the fault within it. Maybe it's because my mind is so old now I can't wrap my head around my own ideas. If someone could please take a look at it and come up with a solution, I would really appreciate it.

Please note that you need libsndfile installed in your system. You can compile my program with "g++ filename.cpp -o filename -lsndfile" or something of the like. Here's the code.

```
#include <sndfile.hh>
#include <iostream>
#include <cmath>
#include <stdlib.h>     /* srand, rand */
#include <time.h>       /* time */

using namespace std ;

class note ;
class piece;
class instrument;
class timbre;

    //const int format=SF_FORMAT_WAV | SF_FORMAT_PCM_16 ;
    const int format=SF_FORMAT_WAV | SF_FORMAT_FLOAT;
    const int channels = 1 ;
    const int sampleRate = 44100 ;
    const char* outfilename = "00029.wav" ;

    int nyquist = sampleRate/2 ;
    float bpm = 89.0 ;
    float bpb = 4.0 ;
    float val = 4.0 ;
    float beat = bpm * 60.0 ;

// frequency 8.2 Hz to 33.5 kHz (pitch 0, 144)
float freq(int pitch) { return pow(2.0,(pitch-69.0)/12.0)*440 ; }
// period
float period(int pitch) { return (1/freq(pitch)) ; }
float period(float f) {return 1/f ; }
// phase -2*M_PI to 2*M_PI rad
float phase(float d) { return M_PI*d ; }
float amplitude(float n) { return 1/n ; }

float attack(float s, float t) {
    float c = s/sampleRate ;
    return (t>0 && c<t) ? c/t : float(1) ; }
float decay(float s, float att, float sus, float t) {
    float c = s/sampleRate ;
    return (c>=att && c<att+t) ? (1-(1-sus)*(c-att)/t) : float(1) ; }
float sustain(float s, float att, float dec, float dur, float l) {
    float c = s/sampleRate ;
    return (c>=att+dec && c<dur) ? l : float (1) ; }
float release(float s, float d, float sus, float t) {
    float c = s/sampleRate ;
    return (t>0 && c>=d) ? (sus)*(1-(c-d)/t) : float(1) ; }

float envelope(float i, float att, float dec, float sus, float rel, float t) {
    return attack(i,att)
        * decay(i,att,sus,dec)
        * sustain(i,att,dec,t,sus)
        * release(i,t,sus,rel); }

void sleep(unsigned int mseconds) {
    clock_t goal = mseconds + clock();
    while (goal > clock()); }

class timbre {
    public  :   timbre() {}
                timbre(unsigned long long int h, unsigned long long int s) {
                    harmonics=h; subharmonics=s;
                    strengthen(); }
                void set(unsigned long long int h, unsigned long long int s) {
                    harmonics=h; subharmonics=s;
                    strengthen(); }
                unsigned long long int harmonics ;
                unsigned long long int subharmonics ;
                float harstrength [64] ;
                float substrength [64] ;
                float pu [64] ;
                float po [64] ;
                float harsh ;
                float subsh ;
                int counter ;
                void strengthen() {
                    counter = 0 ;
                    harsh = 1.0 ;
                    subsh = 1.0 ;
                    srand (time(NULL)) ;
                    unsigned long long int c=1;
                    for (int i=0; i<64; i++) {
                        if (c&harmonics) {
                            pu[i] = phase((float)rand()/RAND_MAX);
                            counter++;
                            harstrength[i]=harsh*(float)rand()/(RAND_MAX) ;
                            harsh=harstrength[i] ; }
                        else
                        harstrength[i]=0;
                        if (c&subharmonics) {
                            po[i] = phase((float)rand()/RAND_MAX);
                            counter++;
                            substrength[i]=harsh*(float)rand()/(RAND_MAX) ;
                            subsh=substrength[i] ; }

                        else
                        substrength[i]=0;
                        c=c<<1; } } };

class instrument {
    public  :   instrument(unsigned int d) {
                    amp = 1.0/(2.0*(d+1)-2.0) ;
                    srand (time(NULL)) ;
                    unsigned long long int g = rand()+2^32*rand() ;
                    unsigned long long int h = rand()+2^32*rand() ;
                    tim.set(g,h) ; }
                float amp ;
                timbre tim ; } ;

class note {
    public :    note() {
                    srand (time(NULL)) ;
                    dur = pow(2,round((float)rand()*16.0/RAND_MAX)-8.0)/bpm ;
                    for (int i=1; i<4 ; i++)
                        if (rand()%2 == 1)
                            dur += pow(2,round((float)rand()*16.0/RAND_MAX)-8.0)
                                /bpm ;
                    if (rand()%2 == 1) {
                        pit = freq(round((float)rand()*144.0/RAND_MAX)) ;
                        amp = (float)rand()/RAND_MAX ;
                        att = dur*(float)rand()/RAND_MAX ;
                        dec = (dur - att)*(float)rand()/RAND_MAX ;
                        sus = (float)rand()/RAND_MAX ;
                        rel = dur * (float)rand()/RAND_MAX ; }
                    else {
                        pit = 0.0 ;
                        amp = 0.0 ;
                        att = 0.0 ;
                        dec = 0.0 ;
                        sus = 0.0 ;
                        rel = 0.0 ; } }
                float pit ;
                float dur ;
                float amp ;
                float att ;
                float dec ;
                float sus ;
                float rel ; } ;


int main() {
    SndfileHandle outfile(outfilename,SFM_WRITE,format,channels,sampleRate) ;
        if (not outfile) return -1 ;
    int len = 2 * pow(2,8) * sampleRate / bpm ;

    int numofinst = 1 ;
cout << "instruments " << numofinst << endl ;
    float buffer[len];
    float buf[len];
    float buf2[len];
    int prelease = 0 ;
    bool bof = false ;
    srand (time(NULL));
    for (int i=0; i<len; i++) {
        buffer[i] = 0 ;
        buf2[i] = 0 ; }
    for (int i=0; i<len; i++) {
        buf[i] = 0; }
    int notes = 1024;

    bool buffull[numofinst] ;
    bool done[numofinst] ;
    bool doneforrealz = false ;
    int i[numofinst] ;
    int pri[numofinst] ;

    instrument * ins[numofinst];
    int amo = 0 ;
    for (int j=0 ; j<numofinst; j++) {
        ins[j] = new instrument(j) ;
        buffull[j] = false ;
        done[j] = false ;
        pri[j] = 0 ;
        i[j] = 0 ; }
    int m=0 ;
    while (m<numofinst && !doneforrealz) {
        int beg = pri[m] ;
        int sta = 0 ;
        pri[m] = 0 ;
        
        for (int r=0; r<numofinst; r++) {
            if(done[r] && r==numofinst-1)
                    doneforrealz = true ;
            else {
                break ;
            }
        }

        if(buffull[m] || done[m]) {
            if (m<(numofinst-1)) {
                m++;
            }
            else {
                if (m == numofinst-1) {
                    for (int p=0; p<numofinst; p++) {
                        if (buffull[p]) {
                            if (p==(numofinst-1)) {
                                outfile.write(&buf[0], len) ;
                                for (int q=0; q<len; q++) {
                                    buf[q] = 0 ; }
                                for (int r=0; r<amo; r++) {
                                    buf[r] = buf2[r] ;
                                    buf2[r] = 0.0 ; }
                                amo = 0 ;
                                for (int q=0; q<numofinst; q++) {
                                    buffull[q] = false;
                                }
                                
                            }

                        }
                        else {
                            if (done[p] && beg>0 && p==(numofinst-1)) {
                                outfile.write(&buf[0], beg) ;
                            }
                            else 
                                break ;
                        }
                    }
                }
            }
        }
        else {
            while (i[m]<notes)
            {
                note n;
                int core = (sampleRate)*(n.dur) ;
                int size = core + (sampleRate)*(n.rel) ;
                float sample[size] ;
                for (int j=0; j<size; j++) {
                    sample[j]=0; }
                if (core<=len && prelease<=len) {
                    for (int j=0; j<prelease; j++) {
                        sample[j]=buffer[j]; }
                    for (int l=0; l<core; l++) {
                        for (int k=0; k<64; k++) {
                            if ((*ins[m]).tim.harstrength[k]!=0.0) {
                            sample[l] = sample[l]
                                    + envelope(l,n.att,n.dec,n.sus,n.rel,n.dur)
                                    * (*ins[m]).amp * n.amp
                                    * (*ins[m]).tim.harstrength[k]
                                    * sin(float(l)/(sampleRate)
                                    * M_PI*n.pit*(k+1.0)
                                    * 2.0+(*ins[m]).tim.pu[k])
                                    / float((*ins[m]).tim.counter) ; } }

                        for (int k=0; k<64; k++) {
                            if ((*ins[m]).tim.substrength[k]!=0.0) {
                            sample[l] = sample[l]
                                    + envelope(l,n.att,n.dec,n.sus,n.rel,n.dur)
                                    * (*ins[m]).amp * n.amp
                                    * (*ins[m]).tim.substrength[k]
                                    * sin(float(l)/(sampleRate)
                                    * M_PI*n.pit/(k+1.0)
                                    * 2.0+(*ins[m]).tim.po[k])
                                    / float((*ins[m]).tim.counter) ; } } }

                    if((beg+core)<=(len)){
                        for (int o=beg; o<beg+core; o++)
                            buf[o] += sample[o-beg] ;
                        beg += core ;
                        pri[m] = beg ;
                    }
                    else {
                        for (int o=beg; o<(len) ; o++)
                            buf[o] += sample[o-beg] ;
                        sta = (len)-beg ;
                        beg = 0 ;
                        pri[m] = core-sta ;
                        amo = max(amo,pri[m]);
                        buffull[m] = true ;
                        for (int o=sta; o<core; o++) {
                            buf2[o-sta] += sample[o];
                            sample[o] = 0.0 ; } }

                    if (core<prelease) {
                        for (int j=core ; j<prelease ; j++) {
                            buffer[j-core] = buffer[j]; }
                        for (int j=(prelease-core); j<prelease; j++) {
                            buffer[j] = 0; }
                        prelease = prelease-core; }
                    else {
                        for (int j=0; j<prelease; j++)
                            buffer[j] = 0;
                        prelease = 0; }

                    for (int j=core; j<size; j++) {
                            for (int k=0; k<64; k++) {
                                if ((*ins[m]).tim.harstrength[k]!=0) {
                                buffer[j-core] = buffer[j-core]
                                        + envelope(j,n.att,n.dec,n.sus,n.rel,n.dur)
                                        * (*ins[m]).amp * n.amp
                                        * (*ins[m]).tim.harstrength[k]
                                        * sin(float(j)/(sampleRate)
                                        * M_PI*n.pit*(k+1.0)
                                        * 2.0+(*ins[m]).tim.pu[k])
                                        / float((*ins[m]).tim.counter) ; } }
                            for (int k=0; k<64; k++) {
                                if ((*ins[m]).tim.substrength[k]!=0) {
                                buffer[j-core] = buffer[j-core]
                                        + envelope(j,n.att,n.dec,n.sus,n.rel,n.dur)
                                        * (*ins[m]).amp * n.amp
                                        * (*ins[m]).tim.substrength[k]
                                        * sin(float(j)/(sampleRate)
                                        * M_PI*n.pit/(k+1.0)
                                        * 2.0+(*ins[m]).tim.po[k])
                                        / float((*ins[m]).tim.counter) ; } } }

                    prelease = max((size - core), prelease); }
                else {
                    bof = true ;
                    cout << "buffer overflow" << endl;
                    return -1 ; 
                }
                i[m]++ ;
                if (i[m]>=notes)
                    done[m] = true ;
                sleep(100000) ; 
            } 
        }
    }     
    if (prelease > 0)
        outfile.write(&buffer[0], prelease) ;

    return 0 ;
}
```

---

### Post by spjackson on 2016-04-24
With some help from the debugger...
ins[0] gets set here:
```

        ins[j] = new instrument(j) ;

```
but when the crash occurs, ins[0] has changed even though there is no code to change it, so ins is being unintentionally overwritten.
```

                float sample[size] ;
                for (int j=0; j<size; j++) {
                    sample[j]=0; }
                if (core<=len && prelease<=len) {
                    for (int j=0; j<prelease; j++) {
                        sample[j]=buffer[j]; }

```
size = 1056
prelease = 2081
Therefore you are writing way beyond sample[size-1] whicb tramples on ins.

---

