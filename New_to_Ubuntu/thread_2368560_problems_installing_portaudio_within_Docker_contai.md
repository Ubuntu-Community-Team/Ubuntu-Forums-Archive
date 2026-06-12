---
title: "problems installing portaudio within Docker container"
date: 2017-08-12
forum: New to Ubuntu
---

### Post by madfock on 2017-08-12
Dear someone, 
I am trying to set up port audio (open source audio library) within a docker container. This is my Dockerfile:

FROM ubuntu:16.04
ADD portaudio /portaudio
ADD source.cpp /source.cpp
RUN apt-get update 
RUN apt-get --fix-missing upgrade 
RUN apt-get -y install --no-install-recommends apt-utils build-essential
RUN apt-get -y install libasound-dev
RUN cd /portaudio && ./configure && make 
RUN cd /portaudio && make install

portaudio is an unzipped directory with the port audio source code (from their website). I expected that when I write make install, this would install portaudio "globally" on my system (Docker environment). This source code:

#include <iostream>
#include "portaudio.h"


int main(){
    std::cout << "init" <<std::endl;
    PaError err = Pa_initialize();
    if(err != paNoError){
        std::cout << "could not initialize" << std::endl;
    } else {
        std::cout << "could initialize" << std::endl;
    }
    return 0;
}

this creates this error: 
[COLOR=#000000][FONT=Menlo]**source.cpp:** In function '**int main()**':[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**source.cpp:7:30:** [COLOR=#c33720]**error: **[/COLOR]'**Pa_initialize**' was not declared in this scope[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  PaError err = Pa_initialize();[/FONT][/COLOR]




do I have to link some .c/.cpp files when compiling or something similar?

---

