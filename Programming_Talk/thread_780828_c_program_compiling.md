---
title: "c program compiling"
date: 2008-05-03
forum: Programming Talk
---

### Post by nbo10 on 2008-05-03
Hi All,
I am trying to get the comedi drivers working on my ubuntu system. I think they are working but I'm having a problem compiling a program to test. The file test2.c is

```
/*
 * A very small one-shot input demo
 * Part of Comedilib
 *
 * Copyright (c) 1999,2000 David A. Schleef <ds@schleef.org>
 *
 * This file may be freely modified, distributed, and combined with
 * other software, as long as proper attribution is given in the
 * source code.
 */
/*
   A little input demo
 */

#include <stdio.h>
#include <comedilib.h>
#include <fcntl.h>
#include <unistd.h>
#include <stdlib.h>
#include <errno.h>
#include <getopt.h>
#include <ctype.h>
#include <math.h>
#include "examples.h"

comedi_t *device;


int main(int argc, char *argv[])
{
	lsampl_t data;
	int ret;
	comedi_range * range_info;
	lsampl_t maxdata;
	double physical_value;
	struct parsed_options options;

	init_parsed_options(&options);
	parse_options(&options, argc, argv);

	device = comedi_open(options.filename);
	if(!device){
		comedi_perror(options.filename);
		exit(-1);
	}

	if(options.verbose){
		printf("measuring device=%s subdevice=%d channel=%d range=%d analog reference=%d\n",
			options.filename, options.subdevice, options.channel, options.range, options.aref);
	}

	ret = comedi_data_read(device, options.subdevice, options.channel, options.range, options.aref, &data);
	if(ret < 0){
		comedi_perror(options.filename);
		exit(-1);
	}

	if(options.physical) {
		comedi_set_global_oor_behavior(COMEDI_OOR_NAN);
		range_info = comedi_get_range(device, options.subdevice, options.channel, options.range);
		maxdata = comedi_get_maxdata(device, options.subdevice, options.channel);
		if(options.verbose) {
			printf("[0,%d] -> [%g,%g]\n", maxdata,
				range_info->min, range_info->max);
		}
		physical_value = comedi_to_phys(data, range_info, maxdata);
		if(isnan(physical_value)) {
			printf("Out of range [%g,%g]",
				range_info->min, range_info->max);
		} else {
			printf("%g", physical_value);
			switch(range_info->unit) {
				case UNIT_volt: printf(" V"); break;
				case UNIT_mA: printf(" mA"); break;
				case UNIT_none: break;
				default: printf(" (unknown unit %d)",
					range_info->unit);
			}
			if(options.verbose) {
				printf(" (%lu raw units)", (unsigned long)data);
			}
		}
	} else {
		printf("%lu", (unsigned long)data);
	}
	printf("\n");

	return 0;
}


```

with the examples.h file, in the same dir

```

#ifndef _EXAMPLES_H
#define _EXAMPLES_H

#include <stdio.h>

/*
 * Definitions of some of the common code.
 */

extern comedi_t *device;

struct parsed_options
{
	char *filename;
	double value;
	int subdevice;
	int channel;
	int aref;
	int range;
	int physical;
	int verbose;
	int n_chan;
	int n_scan;
	double freq;
};

extern void init_parsed_options(struct parsed_options *options);
extern int parse_options(struct parsed_options *options, int argc, char *argv[]);
extern char *cmd_src(int src,char *buf);
extern void dump_cmd(FILE *file,comedi_cmd *cmd);
/* some helper functions used primarily for counter demos */
extern int arm(comedi_t *device, unsigned subdevice, lsampl_t source);
extern int reset_counter(comedi_t *device, unsigned subdevice);
extern int set_counter_mode(comedi_t *device, unsigned subdevice, lsampl_t mode_bits);
extern int set_clock_source(comedi_t *device, unsigned subdevice, lsampl_t clock, lsampl_t period_ns);
extern int set_gate_source(comedi_t *device, unsigned subdevice, lsampl_t gate_index, lsampl_t gate_source);
extern int comedi_internal_trigger(comedi_t *dev, unsigned int subd, unsigned int trignum);

#define sec_to_nsec(x) ((x)*1000000000)
#define sec_to_usec(x) ((x)*1000000)
#define sec_to_msec(x) ((x)*1000)
#define msec_to_nsec(x) ((x)*1000000)
#define msec_to_usec(x) ((x)*1000)
#define usec_to_nsec(x) ((x)*1000)

#endif

```

I compile it with 

```
 gcc test2.c -lcomedi -o test2 -lm
```

with the following error

```
/tmp/ccyJbSzU.o: In function `main':
test2.c:(.text+0x1d): undefined reference to `init_parsed_options'
test2.c:(.text+0x35): undefined reference to `parse_options'
collect2: ld returned 1 exit status

```

---

### Post by Joeb454 on 2008-05-03
Do you have an examples.o file? You most likely need to tell the compiler to include it. I have app's with a custom header file, I need to include custom.o for example by running
```
gcc prog1.c ./custom.o -o prog1
```

---

### Post by Coso on 2008-05-07
Just a thought: I seem to remember that the comedi demo directory contains an additional source code file (common.c?) that contains the missing functions. Try something like
gcc test2.c common.c -lcomedi -o test2 -lm
I don't have a comedi distribution with me at the moment, so forgive me if this is nonsense...

---

