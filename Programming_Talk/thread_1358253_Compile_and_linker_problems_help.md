---
title: "Compile and linker problems: help"
date: 2009-12-18
forum: Programming Talk
---

### Post by erotavlas on 2009-12-18
Hi,

I have written this C code that work well as stand-alone software. I'm trying to integrate it on a preexisting software, but without success.

The code is the following
```

#include "wand/magick_wand.h"

void DrawText(char *inputImage, char *outputImage, char *outputFormat, char *conferenceName, char *data, char *userName, char *userID) {

    MagickBooleanType status;
    MagickWand *magick_wand = NULL;
    DrawingWand *d_wand = NULL;
    PixelWand *p_wand = NULL;

  **  magick_wand = NewMagickWand();**
    d_wand = NewDrawingWand();
    p_wand = NewPixelWand();

    // fixed data
    char *user = "Utente";
    char *ID = "ID";

    // initialize MagickWand environment
    MagickWandGenesis();
    
    // Read the image. 
    status = MagickReadImage(magick_wand, inputImage);
    if (status == MagickFalse) {
        printf("Unable to Read\n");
        //ThrowWandException(magick_wand);
    }
    
    // Scale the image dimension
    if (strcmp(outputFormat,"CIF") == 0) 
        status = MagickScaleImage(magick_wand, 352, 288);
    else if (strcmp(outputFormat,"QCIF") == 0) 
        status = MagickScaleImage(magick_wand, 176, 144);
    else 
        printf("Invalid output format %s\n", outputFormat);

    if (status == MagickFalse) {
        printf("Unable to Scale\n");
        //ThrowWandException(magick_wand);
    }
        
    // Set up the font size and colour
    DrawSetFont(d_wand,"Helvetica");
    PixelSetColor(p_wand,"black");
    DrawSetFillColor(d_wand,p_wand);
    DrawSetFontSize(d_wand,28);
    // Now draw the text
    DrawAnnotation(d_wand,10,50,(const unsigned char *) conferenceName);

    DrawSetFontSize(d_wand,14);
    DrawAnnotation(d_wand,150,15,(const unsigned char *) data);
    // different font, colour and size
    PixelSetColor(p_wand,"green");
    DrawSetFillColor(d_wand,p_wand);
    DrawSetFontSize(d_wand,20);
    DrawSetFont(d_wand,"Times-Roman");
    // Now draw the text
    DrawAnnotation(d_wand,30,90,(const unsigned char *) user);

    // same size and colour
    DrawSetFont(d_wand,"Times-Roman");
    DrawAnnotation(d_wand,180,90,(const unsigned char *) ID);

    // Draw the image on to the magick_wand
    MagickDrawImage(magick_wand, d_wand);

    // and write it
    status = MagickWriteImage(magick_wand, outputImage);

    /* Clean up */
    if (status == MagickFalse)
        //ThrowWandException(magick_wand);
    if(magick_wand) magick_wand = DestroyMagickWand(magick_wand);
    if(d_wand) d_wand = DestroyDrawingWand(d_wand);
    if(p_wand) p_wand = DestroyPixelWand(p_wand);
    
    // terminate the MagickWand environment
    MagickWandTerminus();
    printf("\n%s,%s,%s,%s,%s,%s\n",inputImage, outputImage, conferenceName, data, userName, userID);
}



```I have understood that the problem is on the call **  magick_wand = NewMagickWand() **...If I make the code more simple as the following
```
void DrawText(char *inputImage, char *outputImage, char *outputFormat, char *conferenceName, char *data, char *userName, char *userID) {

    MagickBooleanType status;
    MagickWand *magick_wand = NULL;
    DrawingWand *d_wand = NULL;
    PixelWand *p_wand = NULL;
 **  magick_wand = NewMagickWand();**



```
It will work only if I comment the line **  magick_wand = NewMagickWand() **. Probably there is a problem on MagickWand function call. It requires external libraries that are passed to linker with -lMagickWand option.

If i try to add or remove the linker option -lMagickWand i don't see any difference during the compilation. :confused:

Can you help me?You are my last chance :rolleyes:

Thanks in advance

NB when i compile the stand-alone code i use the following command gcc -Wall -lMagickWand wand.c -0 wand. when i compile the preexisting software there is a Makefile that define the compilation and linkage parameters.


PS

In the Makefile there are a lot of lines...I carry these concerning the compilation.

```

.EXPORT_ALL_VARIABLES:

#
# app_conference defines which can be passed on the command-line
#

INSTALL_PREFIX :=
INSTALL_MODULES_DIR := $(INSTALL_PREFIX)/usr/lib/asterisk/modules

ASTERISK_INCLUDE_DIR ?= ../asterisk/include

REVISION = $(shell svnversion -n .)

# turn app_conference debugging on or off ( 0 == OFF, 1 == ON )
APP_CONFERENCE_DEBUG ?= 0

# 0 = OFF 1 = astdsp 2 = speex
SILDET := 2

# turn app_conference Dummy User on or off ( 0 == OFF, 1 == ON )
APP_CONFERENCE_DU ?= 1

#
# app_conference objects to build
#

OBJS = app_conference.o conference.o member.o frame.o cli.o 
TARGET = app_conference.so


#
# standard compile settings
#

PROC = $(shell uname -m)
INSTALL = install

INCLUDE = -I$(ASTERISK_INCLUDE_DIR)
DEBUG := -g

CFLAGS = -pipe -Wall -Wmissing-prototypes -Wmissing-declarations -MD -MP $(DEBUG)

CPPFLAGS = $(INCLUDE) -D_REENTRANT -D_GNU_SOURCE -DREVISION=\"$(REVISION)\"


[B]ifeq ($(APP_CONFERENCE_DEBUG), 1)
CPPFLAGS += -DAPP_CONFERENCE_DEBUG
endif[/B]


ifeq ($(APP_CONFERENCE_DU), 1)
CPPFLAGS += -lMagickWand 
OBJS += stream.o
endif

#
# additional flag values for silence detection
#


OSARCH=$(shell uname -s)
ifeq (${OSARCH},Darwin)
SOLINK=-dynamic -bundle -undefined suppress -force_flat_namespace
else
SOLINK=-shared -Xlinker -x
endif

DEPS += $(subst .o,.d,$(OBJS))

#
# targets
#

all: $(TARGET)

.PHONY: clean
clean:
    $(RM) $(OBJS) $(DEPS)

.PHONY: distclean
distclean: clean
    $(RM) $(TARGET)

#stream.o: stream.c gcc -Wall -lMagickWand stream.c

$(TARGET): $(OBJS)
    $(CC) -pg $(SOLINK) -o $@ $(OBJS)



vad_test: vad_test.o libspeex/preprocess.o libspeex/misc.o libspeex/smallft.o
    $(CC) $(PROFILE) -o $@ $^ -lm

install:
    $(INSTALL) -m 755 $(TARGET) $(INSTALL_MODULES_DIR)


-include $(DEPS)

```I have added the following lines...
```
ifeq ($(APP_CONFERENCE_DU), 1)
CPPFLAGS += -lMagickWand 
OBJS += stream.o
endif
```

---

### Post by dwhitney67 on 2009-12-18
You provided 2/3 of the information that is needed; the other 1/3, which is missing, is the actual error message that you are getting.  It would be most helpful if you would post this error message.

I presume it is a compilation problem based on this statement:
> 
If i try to add or remove the linker option -lMagickWand i don't see any difference during the compilation. 


---

### Post by erotavlas on 2009-12-18
> **dwhitney67 said:**
> You provided 2/3 of the information that is needed; the other 1/3, which is missing, is the actual error message that you are getting.  It would be most helpful if you would post this error message.

I presume it is a compilation problem based on this statement:

The problem is that there isn't a error message.

My stand-alone code compiled without -lMagickwand option return the following error

```

gcc -Wall stream.c -o stream
stream.c:13:1: warning: multi-line comment
/tmp/ccYcwKL5.o: In function `DrawText':
stream.c:(.text+0x1c): undefined reference to `NewMagickWand'
stream.c:(.text+0x24): undefined reference to `NewDrawingWand'
stream.c:(.text+0x2c): undefined reference to `NewPixelWand'
stream.c:(.text+0x42): undefined reference to `MagickWandGenesis'
stream.c:(.text+0x54): undefined reference to `MagickReadImage'
stream.c:(.text+0x9b): undefined reference to `MagickScaleImage'
stream.c:(.text+0xd2): undefined reference to `MagickScaleImage'
stream.c:(.text+0x110): undefined reference to `DrawSetFont'
stream.c:(.text+0x123): undefined reference to `PixelSetColor'
stream.c:(.text+0x135): undefined reference to `DrawSetFillColor'
stream.c:(.text+0x14a): undefined reference to `DrawSetFontSize'
stream.c:(.text+0x170): undefined reference to `DrawAnnotation'
stream.c:(.text+0x185): undefined reference to `DrawSetFontSize'
stream.c:(.text+0x1ab): undefined reference to `DrawAnnotation'
stream.c:(.text+0x1be): undefined reference to `PixelSetColor'
stream.c:(.text+0x1d0): undefined reference to `DrawSetFillColor'
stream.c:(.text+0x1e5): undefined reference to `DrawSetFontSize'
stream.c:(.text+0x1f8): undefined reference to `DrawSetFont'
stream.c:(.text+0x21e): undefined reference to `DrawAnnotation'
stream.c:(.text+0x231): undefined reference to `DrawSetFont'
stream.c:(.text+0x257): undefined reference to `DrawAnnotation'
stream.c:(.text+0x269): undefined reference to `MagickDrawImage'
stream.c:(.text+0x27b): undefined reference to `MagickWriteImage'
stream.c:(.text+0x295): undefined reference to `DestroyMagickWand'
stream.c:(.text+0x2a9): undefined reference to `DestroyDrawingWand'
stream.c:(.text+0x2bd): undefined reference to `DestroyPixelWand'
stream.c:(.text+0x2c5): undefined reference to `MagickWandTerminus'
collect2: ld returned 1 exit status

```If i add the following lines to the Makefile of preexisting code

```
ifeq ($(APP_CONFERENCE_DU), 1)
CPPFLAGS += -lMagickWand 
OBJS += stream.o
endif 
```I don't get compilation or linking error...If i comment the CPPFLAGS += -lMagickWand the result doesn't change. :(
When i run the preexisting application it doesn't start, but there is no error. There is a message in Asterisk CLI:

```

WARNING[6163]: pbx.c:3677 pbx_extension_helper: No application 'Conference' for extension (users, 9999, 1)


```
I have discovered (I'm sure) that the problem is at the call of external library NewMagickwand(). I think that the Makefile is wrong but i don't understand where...

PS
The preexisting application is Asterisk 1.6.2 with app_conference 2.0.1 plug-in they work well together. Now i'm trying to add a new feature to app_conference.

---

### Post by dwhitney67 on 2009-12-18
Ok... I see the problem... you are confusing 'compiling' with 'linking'.  They occur in separate stages.

Adding MagicWand to CPPFLAGS makes no difference; this variable is only used during compilation of a source file to make object file.

When you link one or more object files together, then you need to specify the -lMagicWand.

In your Makefile, you do not seem to have a variable for storing the list of the libraries you wish to link against.  Typically it looks something like:
```

LIBS = -lMagicWand -lm

...

# here is where the program, APP, is linked
#
$(APP): $(OBJS)
        $(CC) $^ $(LIBS) -o $@

...

```
P.S.  I don't know if the math library is needed; I only put it above because it appears in your Makefile.

---

### Post by erotavlas on 2009-12-18
You are a phenomenon while i'm a quite stupid...I'm finding the solution, but you are faster than me.

Thank you very much

---

