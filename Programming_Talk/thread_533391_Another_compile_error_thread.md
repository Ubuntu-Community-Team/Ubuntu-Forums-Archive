---
title: "Another compile error thread"
date: 2007-08-23
forum: Programming Talk
---

### Post by somafm on 2007-08-23
Hello, yet another 'compile error' thread :-P

I have build-essentials installed, but still no go. I have also tried using the g++ command instead of gcc, and it still didn't work. I really don't know anything about c programming, I just want to get this CLI application working in Ubuntu. Any ideas? Thanks so much! 8-)

**_file: key2pb.c_**```
/*
    Copyright 2004,2005,2006,2007 Luigi Auriemma

    This program is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program; if not, write to the Free Software
    Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307 USA

    http://www.gnu.org/licenses/gpl.txt
*/

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "pbmd5.cpp"

typedef uint8_t     u8;
typedef uint16_t    u16;
typedef uint32_t    u32;



#define VER         "0.3"



u32      aa[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x000006bf, 0xbed3dd55, 0x1, 0x0 };
u32  bf1942[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0xb2a705c9, 0x1, 0x0 };
u32     bf2[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d1007df, 0x000000df, 0x8d72af09, 0xb518aa83, 0x1, 0x0 };
u32  bf2142[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x000006ad, 0xbe6d7c8f, 0x1, 0x0 };
u32     bfv[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0xb2acb5d4, 0x1, 0x0 };
u32     cod[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x000006be, 0xbece2d4a, 0x00051a56, 0x1, 0x0 };
u32    cod2[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x000006bd, 0xbec87d3f, 0x00051a56, 0x1, 0x0 };
u32   doom3[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0xb32426bb, 0x00051a56, 0x1, 0x0 };
u32      et[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x000005f3, 0xba4b9491, 0x00051a56, 0x1, 0x0 };
u32  farcry[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0xb2f0f658, 0x1, 0x0 };
u32    fear[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x000006b4, 0xbe954cdc, 0x00051a56, 0x1, 0x0 };
u32   mohpa[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x987570ee, 0x00051a56, 0x987570ee, 0x1, 0x0 };
u32    prey[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0xb4a6e9a7, 0x00051a56, 0x1, 0x0 };
u32  quake3[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x000006c2, 0xbee4ed76, 0x000017b5, 0x00051a56, 0x1, 0x0 };
u32  quake4[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0xb529baa4, 0x00051a56, 0x1, 0x0 };
u32     r63[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0xb35d0729, 0xb35d0729, 0x1, 0x0 };
u32     r64[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0xb0e5b264, 0x00051a56, 0xb0e5b264, 0x1, 0x0 };
u32     r65[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x1, 0x0 };
u32    rtcw[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x000005f5, 0xba56f4a7, 0x00051a56, 0x1, 0x0 };
u32    sof2[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x00051a56, 0x1, 0x0 };
u32      uo[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0xb3aca7c3, 0x00051a56, 0x1, 0x0 };
u32 warrock[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x000006c0, 0xbed98d60, 0x8b1006f4, 0x00051a56, 0x1, 0x0 };
u32    scpt[] = { 0x00b684a3, 0x1, 0x0 };
u32    etqw[] = { 0x3b9ac617, 0x3b9ac616, 0x054c4085, 0x00b684a3, 0x8d72af09, 0x000006c1, 0xbedf3d6b, 0x00051a56, 0x1, 0x0 };



void do_md5_game(u8 *gamename, u32 *seed, u8 *key);
void do_md5(u8 *key, u32 seed);



int main(int argc, char *argv[]) {
    int     i;
    u8      *key1,
            *key2,
            *p1,
            *p2,
            *k;

    setbuf(stdout, NULL);

    fputs("\n"
        "Cdkey to Punkbuster GUID "VER"\n"
        "by Luigi Auriemma\n"
        "e-mail: aluigi@autistici.org\n"
        "web:    aluigi.org\n"
        "\n", stdout);

    if(argc < 2) {
        printf("\n"
            "Usage: %s <cdkey>\n"
            "\n"
            "Note: this tool will compute all the MD5 hashes available for each game using\n"
            "      both the cdkey as is and in lower case and without the '-' char\n"
            "      the best way to know the what is the exact seed used by your specific\n"
            "      game is trying to use your cdkey and comparing the hashes with your\n"
            "      pb_g_guid and pb_guid.\n"
            "      Usually the most used seeds are 00b684a3 and 00051a56\n"
            "\n", argv[0]);
        exit(1);
    }

    key1 = strdup(argv[1]);
    key2 = strdup(argv[1]);

    for(p1 = key1, p2 = key2; *p1; p1++) {
        if(*p1 == '-') continue;
        if((*p1 >= 'A') && (*p1 <= 'Z')) {
            *p2++ = *p1 + 32;
        } else {
            *p2++ = *p1;
        }
    }
    *p2 = 0;

    for(i = 0; i < 2; i++) {
        k = key1;
        if(i == 1) k = key2;

        printf("\n- CDKEY    %s\n", k);

        do_md5_game("America's Army",                   aa,         k);
        do_md5_game("Battlefield 1942",                 bf1942,     k);
        do_md5_game("Battlefield 2",                    bf2,        k);
        do_md5_game("Battlefield 2142",                 bf2142,     k);
        do_md5_game("Battlefield Vietnam",              bfv,        k);
        do_md5_game("Call of Duty",                     cod,        k);
        do_md5_game("Call of Duty 2",                   cod2,       k);
        do_md5_game("Doom 3",                           doom3,      k);
        do_md5_game("Enemy Territory",                  et,         k);
        do_md5_game("Enemy Territory: Quake Wars",      etqw,       k);
        do_md5_game("FarCry",                           farcry,     k);
        do_md5_game("F.E.A.R.",                         fear,       k);
        do_md5_game("Medal of Honor: Pacific Assault",  mohpa,      k);
        do_md5_game("Prey",                             prey,       k);
        do_md5_game("Quake 3",                          quake3,     k);
        do_md5_game("Quake 4",                          quake4,     k);
        do_md5_game("Rainbow Six 3: Raven Shield",      r63,        k);
        do_md5_game("Rainbow Six 4: Lockdown",          r64,        k);
        do_md5_game("Rainbow Six 5: Vegas",             r65,        k);
        do_md5_game("Return to Castle Wolfenstein",     rtcw,       k);
        do_md5_game("Soldier of Fortune II",            sof2,       k);
        do_md5_game("Splinter Cell: Pandora Tomorrow",  scpt,       k);
        do_md5_game("Ultima Online",                    uo,         k);
        do_md5_game("WarRock",                          warrock,    k);
    }

    return(0);
}



void do_md5_game(u8 *gamename, u32 *seed, u8 *key) {
    int     i;

    printf("\n  %s:\n", gamename);
    for(i = 0; ; i++) {
        do_md5(key, seed[i]);
        if(!seed[i]) break;
    }
}



void do_md5(u8 *key, u32 seed) {
    MD5_CTX     ctx;
    int         i;
    char        hash[33];
    static const char   hex[16] = "0123456789abcdef";

    MD5Init(&ctx, seed);
    MD5Update(&ctx, key, strlen(key));
    MD5Final(&ctx);

    for(i = 0; i < 16; i++) {
        hash[i << 1]       = hex[ctx.digest[i] >> 4];
        hash[(i << 1) + 1] = hex[ctx.digest[i] & 15];
    }
    hash[i << 1] = 0;

    printf("    %08x %s\n", seed, hash);
}


```
**_file: pbmd5.cpp_**```
//
// PunkBuster Implementation of MD5 by RSA Data Security, Inc.
//

//
// md5.h
//
// style modified by Tony Ray, January 2001
// added support for randomizing initialization constants in MD5Init()

/*
 **********************************************************************
 ** md5.h -- Header file for implementation of MD5                   **
 ** RSA Data Security, Inc. MD5 Message Digest Algorithm             **
 ** Created: 2/17/90 RLR                                             **
 ** Revised: 12/27/90 SRD,AJ,BSK,JT Reference C version              **
 ** Revised (for MD5): RLR 4/27/91                                   **
 **   -- G modified to have y&~z instead of y&z                      **
 **   -- FF, GG, HH modified to add in last register done            **
 **   -- Access pattern: round 2 works mod 5, round 3 works mod 3    **
 **   -- distinct additive constant for each step                    **
 **   -- round 4 added, working mod 7                                **
 **********************************************************************
 */

/*
 **********************************************************************
 ** Copyright (C) 1990, RSA Data Security, Inc. All rights reserved. **
 **                                                                  **
 ** License to copy and use this software is granted provided that   **
 ** it is identified as the "RSA Data Security, Inc. MD5 Message     **
 ** Digest Algorithm" in all material mentioning or referencing this **
 ** software or this function.                                       **
 **                                                                  **
 ** License is also granted to make and use derivative works         **
 ** provided that such works are identified as "derived from the RSA **
 ** Data Security, Inc. MD5 Message Digest Algorithm" in all         **
 ** material mentioning or referencing the derived work.             **
 **                                                                  **
 ** RSA Data Security, Inc. makes no representations concerning      **
 ** either the merchantability of this software or the suitability   **
 ** of this software for any particular purpose.  It is provided "as **
 ** is" without express or implied warranty of any kind.             **
 **                                                                  **
 ** These notices must be retained in any copies of any part of this **
 ** documentation and/or software.                                   **
 **********************************************************************
 */

/* typedef a 32 bit type */
typedef unsigned long int UINT4;

/* Data structure for MD5 (Message Digest) computation */
typedef struct {
  UINT4 i[2];                   /* number of _bits_ handled mod 2^64 */
  UINT4 buf[4];                                    /* scratch buffer */
  unsigned char in[64];                              /* input buffer */
  unsigned char digest[16];     /* actual digest after MD5Final call */
} MD5_CTX;

void MD5Init (MD5_CTX *mdContext, unsigned long pseudoRandomNumber ) ;
void MD5Update (MD5_CTX *mdContext, unsigned char *inBuf, unsigned int inLen) ;
void MD5Final (MD5_CTX *mdContext) ;

//
// md5.cpp
//
// style modified by Tony Ray, January 2001
// added support for randomizing initialization constants in MD5Init()

/*
 **********************************************************************
 ** md5.c                                                            **
 ** RSA Data Security, Inc. MD5 Message Digest Algorithm             **
 ** Created: 2/17/90 RLR                                             **
 ** Revised: 1/91 SRD,AJ,BSK,JT Reference C Version                  **
 **********************************************************************
 */

/*
 **********************************************************************
 ** Copyright (C) 1990, RSA Data Security, Inc. All rights reserved. **
 **                                                                  **
 ** License to copy and use this software is granted provided that   **
 ** it is identified as the "RSA Data Security, Inc. MD5 Message     **
 ** Digest Algorithm" in all material mentioning or referencing this **
 ** software or this function.                                       **
 **                                                                  **
 ** License is also granted to make and use derivative works         **
 ** provided that such works are identified as "derived from the RSA **
 ** Data Security, Inc. MD5 Message Digest Algorithm" in all         **
 ** material mentioning or referencing the derived work.             **
 **                                                                  **
 ** RSA Data Security, Inc. makes no representations concerning      **
 ** either the merchantability of this software or the suitability   **
 ** of this software for any particular purpose.  It is provided "as **
 ** is" without express or implied warranty of any kind.             **
 **                                                                  **
 ** These notices must be retained in any copies of any part of this **
 ** documentation and/or software.                                   **
 **********************************************************************
 */

//#include "md5.h"

static unsigned char PADDING[64] = {
  0x80, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00,
  0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00,
  0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00,
  0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00,
  0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00,
  0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00,
  0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00,
  0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00
};

/* F, G and H are basic MD5 functions: selection, majority, parity */
#define F(x, y, z) (((x) & (y)) | ((~x) & (z)))
#define G(x, y, z) (((x) & (z)) | ((y) & (~z)))
#define H(x, y, z) ((x) ^ (y) ^ (z))
#define I(x, y, z) ((y) ^ ((x) | (~z))) 

/* ROTATE_LEFT rotates x left n bits */
#define ROTATE_LEFT(x, n) (((x) << (n)) | ((x) >> (32-(n))))

/* FF, GG, HH, and II transformations for rounds 1, 2, 3, and 4 */
/* Rotation is separate from addition to prevent recomputation */

#define FF(a, b, c, d, x, s, ac) {(a) += F ((b), (c), (d)) + (x) + (UINT4)(ac); (a) = ROTATE_LEFT ((a), (s)); (a) += (b); }
#define GG(a, b, c, d, x, s, ac) {(a) += G ((b), (c), (d)) + (x) + (UINT4)(ac); (a) = ROTATE_LEFT ((a), (s)); (a) += (b); }
#define HH(a, b, c, d, x, s, ac) {(a) += H ((b), (c), (d)) + (x) + (UINT4)(ac); (a) = ROTATE_LEFT ((a), (s)); (a) += (b); }
#define II(a, b, c, d, x, s, ac) {(a) += I ((b), (c), (d)) + (x) + (UINT4)(ac); (a) = ROTATE_LEFT ((a), (s)); (a) += (b); }


/* Basic MD5 step. Transform buf based on in.
 */
static void Transform (UINT4 *buf, UINT4 *in)
{
  UINT4 a = buf[0], b = buf[1], c = buf[2], d = buf[3];

  /* Round 1 */
#define S11 7
#define S12 12
#define S13 17
#define S14 22
  FF ( a, b, c, d, in[ 0], S11, (UINT4) 3614090360u); /* 1 */
  FF ( d, a, b, c, in[ 1], S12, (UINT4) 3905402710u); /* 2 */
  FF ( c, d, a, b, in[ 2], S13, (UINT4)  606105819u); /* 3 */
  FF ( b, c, d, a, in[ 3], S14, (UINT4) 3250441966u); /* 4 */
  FF ( a, b, c, d, in[ 4], S11, (UINT4) 4118548399u); /* 5 */
  FF ( d, a, b, c, in[ 5], S12, (UINT4) 1200080426u); /* 6 */
  FF ( c, d, a, b, in[ 6], S13, (UINT4) 2821735955u); /* 7 */
  FF ( b, c, d, a, in[ 7], S14, (UINT4) 4249261313u); /* 8 */
  FF ( a, b, c, d, in[ 8], S11, (UINT4) 1770035416u); /* 9 */
  FF ( d, a, b, c, in[ 9], S12, (UINT4) 2336552879u); /* 10 */
  FF ( c, d, a, b, in[10], S13, (UINT4) 4294925233u); /* 11 */
  FF ( b, c, d, a, in[11], S14, (UINT4) 2304563134u); /* 12 */
  FF ( a, b, c, d, in[12], S11, (UINT4) 1804603682u); /* 13 */
  FF ( d, a, b, c, in[13], S12, (UINT4) 4254626195u); /* 14 */
  FF ( c, d, a, b, in[14], S13, (UINT4) 2792965006u); /* 15 */
  FF ( b, c, d, a, in[15], S14, (UINT4) 1236535329u); /* 16 */

  /* Round 2 */
#define S21 5
#define S22 9
#define S23 14
#define S24 20
  GG ( a, b, c, d, in[ 1], S21, (UINT4) 4129170786u); /* 17 */
  GG ( d, a, b, c, in[ 6], S22, (UINT4) 3225465664u); /* 18 */
  GG ( c, d, a, b, in[11], S23, (UINT4)  643717713u); /* 19 */
  GG ( b, c, d, a, in[ 0], S24, (UINT4) 3921069994u); /* 20 */
  GG ( a, b, c, d, in[ 5], S21, (UINT4) 3593408605u); /* 21 */
  GG ( d, a, b, c, in[10], S22, (UINT4)   38016083u); /* 22 */
  GG ( c, d, a, b, in[15], S23, (UINT4) 3634488961u); /* 23 */
  GG ( b, c, d, a, in[ 4], S24, (UINT4) 3889429448u); /* 24 */
  GG ( a, b, c, d, in[ 9], S21, (UINT4)  568446438u); /* 25 */
  GG ( d, a, b, c, in[14], S22, (UINT4) 3275163606u); /* 26 */
  GG ( c, d, a, b, in[ 3], S23, (UINT4) 4107603335u); /* 27 */
  GG ( b, c, d, a, in[ 8], S24, (UINT4) 1163531501u); /* 28 */
  GG ( a, b, c, d, in[13], S21, (UINT4) 2850285829u); /* 29 */
  GG ( d, a, b, c, in[ 2], S22, (UINT4) 4243563512u); /* 30 */
  GG ( c, d, a, b, in[ 7], S23, (UINT4) 1735328473u); /* 31 */
  GG ( b, c, d, a, in[12], S24, (UINT4) 2368359562u); /* 32 */

  /* Round 3 */
#define S31 4
#define S32 11
#define S33 16
#define S34 23
  HH ( a, b, c, d, in[ 5], S31, (UINT4) 4294588738u); /* 33 */
  HH ( d, a, b, c, in[ 8], S32, (UINT4) 2272392833u); /* 34 */
  HH ( c, d, a, b, in[11], S33, (UINT4) 1839030562u); /* 35 */
  HH ( b, c, d, a, in[14], S34, (UINT4) 4259657740u); /* 36 */
  HH ( a, b, c, d, in[ 1], S31, (UINT4) 2763975236u); /* 37 */
  HH ( d, a, b, c, in[ 4], S32, (UINT4) 1272893353u); /* 38 */
  HH ( c, d, a, b, in[ 7], S33, (UINT4) 4139469664u); /* 39 */
  HH ( b, c, d, a, in[10], S34, (UINT4) 3200236656u); /* 40 */
  HH ( a, b, c, d, in[13], S31, (UINT4)  681279174u); /* 41 */
  HH ( d, a, b, c, in[ 0], S32, (UINT4) 3936430074u); /* 42 */
  HH ( c, d, a, b, in[ 3], S33, (UINT4) 3572445317u); /* 43 */
  HH ( b, c, d, a, in[ 6], S34, (UINT4)   76029189u); /* 44 */
  HH ( a, b, c, d, in[ 9], S31, (UINT4) 3654602809u); /* 45 */
  HH ( d, a, b, c, in[12], S32, (UINT4) 3873151461u); /* 46 */
  HH ( c, d, a, b, in[15], S33, (UINT4)  530742520u); /* 47 */
  HH ( b, c, d, a, in[ 2], S34, (UINT4) 3299628645u); /* 48 */

  /* Round 4 */
#define S41 6
#define S42 10
#define S43 15
#define S44 21
  II ( a, b, c, d, in[ 0], S41, (UINT4) 4096336452u); /* 49 */
  II ( d, a, b, c, in[ 7], S42, (UINT4) 1126891415u); /* 50 */
  II ( c, d, a, b, in[14], S43, (UINT4) 2878612391u); /* 51 */
  II ( b, c, d, a, in[ 5], S44, (UINT4) 4237533241u); /* 52 */
  II ( a, b, c, d, in[12], S41, (UINT4) 1700485571u); /* 53 */
  II ( d, a, b, c, in[ 3], S42, (UINT4) 2399980690u); /* 54 */
  II ( c, d, a, b, in[10], S43, (UINT4) 4293915773u); /* 55 */
  II ( b, c, d, a, in[ 1], S44, (UINT4) 2240044497u); /* 56 */
  II ( a, b, c, d, in[ 8], S41, (UINT4) 1873313359u); /* 57 */
  II ( d, a, b, c, in[15], S42, (UINT4) 4264355552u); /* 58 */
  II ( c, d, a, b, in[ 6], S43, (UINT4) 2734768916u); /* 59 */
  II ( b, c, d, a, in[13], S44, (UINT4) 1309151649u); /* 60 */
  II ( a, b, c, d, in[ 4], S41, (UINT4) 4149444226u); /* 61 */
  II ( d, a, b, c, in[11], S42, (UINT4) 3174756917u); /* 62 */
  II ( c, d, a, b, in[ 2], S43, (UINT4)  718787259u); /* 63 */
  II ( b, c, d, a, in[ 9], S44, (UINT4) 3951481745u); /* 64 */

  buf[0] += a;
  buf[1] += b;
  buf[2] += c;
  buf[3] += d;
}

void MD5Init (MD5_CTX *mdContext, unsigned long pseudoRandomNumber )
{
  mdContext->i[0] = mdContext->i[1] = (UINT4)0;

  /* Load magic initialization constants.
   */
  mdContext->buf[0] = (UINT4)0x67452301 + pseudoRandomNumber * 11 ;
  mdContext->buf[1] = (UINT4)0xefcdab89 + pseudoRandomNumber * 71 ;
  mdContext->buf[2] = (UINT4)0x98badcfe + pseudoRandomNumber * 37 ;
  mdContext->buf[3] = (UINT4)0x10325476 + pseudoRandomNumber * 97 ;
}

void MD5Update (MD5_CTX *mdContext, unsigned char *inBuf, unsigned int inLen)
{
  UINT4 in[16];
  int mdi;
  unsigned int i, ii;

  /* compute number of bytes mod 64 */
  mdi = (int)((mdContext->i[0] >> 3) & 0x3F);

  /* update number of bits */
  if ((mdContext->i[0] + ((UINT4)inLen << 3)) < mdContext->i[0])
    mdContext->i[1]++;
  mdContext->i[0] += ((UINT4)inLen << 3);
  mdContext->i[1] += ((UINT4)inLen >> 29);

  while (inLen--) {
    /* add new character to buffer, increment mdi */
    mdContext->in[mdi++] = *inBuf++;

    /* transform if necessary */
    if (mdi == 0x40) {
      for (i = 0, ii = 0; i < 16; i++, ii += 4)
        in[i] = (((UINT4)mdContext->in[ii+3]) << 24) |
                (((UINT4)mdContext->in[ii+2]) << 16) |
                (((UINT4)mdContext->in[ii+1]) << 8) |
                ((UINT4)mdContext->in[ii]);
      Transform (mdContext->buf, in);
      mdi = 0;
    }
  }
}

void MD5Final (MD5_CTX *mdContext)
{
  UINT4 in[16];
  int mdi;
  unsigned int i, ii;
  unsigned int padLen;

  /* save number of bits */
  in[14] = mdContext->i[0];
  in[15] = mdContext->i[1];

  /* compute number of bytes mod 64 */
  mdi = (int)((mdContext->i[0] >> 3) & 0x3F);

  /* pad out to 56 mod 64 */
  padLen = (mdi < 56) ? (56 - mdi) : (120 - mdi);
  MD5Update (mdContext, PADDING, padLen);

  /* append length in bits and transform */
  for (i = 0, ii = 0; i < 14; i++, ii += 4)
    in[i] = (((UINT4)mdContext->in[ii+3]) << 24) |
            (((UINT4)mdContext->in[ii+2]) << 16) |
            (((UINT4)mdContext->in[ii+1]) << 8) |
            ((UINT4)mdContext->in[ii]);
  Transform (mdContext->buf, in);

  /* store buffer in digest */
  for (i = 0, ii = 0; i < 4; i++, ii += 4) {
    mdContext->digest[ii] = (unsigned char)(mdContext->buf[i] & 0xFF);
    mdContext->digest[ii+1] =
      (unsigned char)((mdContext->buf[i] >> 8) & 0xFF);
    mdContext->digest[ii+2] =
      (unsigned char)((mdContext->buf[i] >> 16) & 0xFF);
    mdContext->digest[ii+3] =
      (unsigned char)((mdContext->buf[i] >> 24) & 0xFF);
  }
}

```



**_output from command: gcc key2pb.c_**```
key2pb.c:26: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘u8’
key2pb.c:27: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘u16’
key2pb.c:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘u32’
key2pb.c:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘aa’
key2pb.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘bf1942’
key2pb.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘bf2’
key2pb.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘bf2142’
key2pb.c:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘bfv’
key2pb.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cod’
key2pb.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cod2’
key2pb.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘doom3’
key2pb.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘et’
key2pb.c:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘farcry’
key2pb.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fear’
key2pb.c:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mohpa’
key2pb.c:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘prey’
key2pb.c:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘quake3’
key2pb.c:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘quake4’
key2pb.c:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r63’
key2pb.c:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r64’
key2pb.c:53: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r65’
key2pb.c:54: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtcw’
key2pb.c:55: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sof2’
key2pb.c:56: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘uo’
key2pb.c:57: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘warrock’
key2pb.c:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘scpt’
key2pb.c:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘etqw’
key2pb.c:63: error: expected ‘)’ before ‘*’ token
key2pb.c:64: error: expected ‘)’ before ‘*’ token
key2pb.c: In function ‘main’:
key2pb.c:70: error: ‘u8’ undeclared (first use in this function)
key2pb.c:70: error: (Each undeclared identifier is reported only once
key2pb.c:70: error: for each function it appears in.)
key2pb.c:70: error: ‘key1’ undeclared (first use in this function)
key2pb.c:71: error: ‘key2’ undeclared (first use in this function)
key2pb.c:72: error: ‘p1’ undeclared (first use in this function)
key2pb.c:73: error: ‘p2’ undeclared (first use in this function)
key2pb.c:74: error: ‘k’ undeclared (first use in this function)
key2pb.c:118: error: ‘aa’ undeclared (first use in this function)
key2pb.c:119: error: ‘bf1942’ undeclared (first use in this function)
key2pb.c:120: error: ‘bf2’ undeclared (first use in this function)
key2pb.c:121: error: ‘bf2142’ undeclared (first use in this function)
key2pb.c:122: error: ‘bfv’ undeclared (first use in this function)
key2pb.c:123: error: ‘cod’ undeclared (first use in this function)
key2pb.c:124: error: ‘cod2’ undeclared (first use in this function)
key2pb.c:125: error: ‘doom3’ undeclared (first use in this function)
key2pb.c:126: error: ‘et’ undeclared (first use in this function)
key2pb.c:127: error: ‘etqw’ undeclared (first use in this function)
key2pb.c:128: error: ‘farcry’ undeclared (first use in this function)
key2pb.c:129: error: ‘fear’ undeclared (first use in this function)
key2pb.c:130: error: ‘mohpa’ undeclared (first use in this function)
key2pb.c:131: error: ‘prey’ undeclared (first use in this function)
key2pb.c:132: error: ‘quake3’ undeclared (first use in this function)
key2pb.c:133: error: ‘quake4’ undeclared (first use in this function)
key2pb.c:134: error: ‘r63’ undeclared (first use in this function)
key2pb.c:135: error: ‘r64’ undeclared (first use in this function)
key2pb.c:136: error: ‘r65’ undeclared (first use in this function)
key2pb.c:137: error: ‘rtcw’ undeclared (first use in this function)
key2pb.c:138: error: ‘sof2’ undeclared (first use in this function)
key2pb.c:139: error: ‘scpt’ undeclared (first use in this function)
key2pb.c:140: error: ‘uo’ undeclared (first use in this function)
key2pb.c:141: error: ‘warrock’ undeclared (first use in this function)
key2pb.c: At top level:
key2pb.c:149: error: expected ‘)’ before ‘*’ token
key2pb.c:161: error: expected ‘)’ before ‘*’ token

```
**_output from command: g++ key2pb.c_**```
key2pb.c:26: error: ‘uint8_t’ does not name a type
key2pb.c:27: error: ‘uint16_t’ does not name a type
key2pb.c:28: error: ‘uint32_t’ does not name a type
key2pb.c:36: error: ‘u32’ does not name a type
key2pb.c:37: error: ‘u32’ does not name a type
key2pb.c:38: error: ‘u32’ does not name a type
key2pb.c:39: error: ‘u32’ does not name a type
key2pb.c:40: error: ‘u32’ does not name a type
key2pb.c:41: error: ‘u32’ does not name a type
key2pb.c:42: error: ‘u32’ does not name a type
key2pb.c:43: error: ‘u32’ does not name a type
key2pb.c:44: error: ‘u32’ does not name a type
key2pb.c:45: error: ‘u32’ does not name a type
key2pb.c:46: error: ‘u32’ does not name a type
key2pb.c:47: error: ‘u32’ does not name a type
key2pb.c:48: error: ‘u32’ does not name a type
key2pb.c:49: error: ‘u32’ does not name a type
key2pb.c:50: error: ‘u32’ does not name a type
key2pb.c:51: error: ‘u32’ does not name a type
key2pb.c:52: error: ‘u32’ does not name a type
key2pb.c:53: error: ‘u32’ does not name a type
key2pb.c:54: error: ‘u32’ does not name a type
key2pb.c:55: error: ‘u32’ does not name a type
key2pb.c:56: error: ‘u32’ does not name a type
key2pb.c:57: error: ‘u32’ does not name a type
key2pb.c:58: error: ‘u32’ does not name a type
key2pb.c:59: error: ‘u32’ does not name a type
key2pb.c:63: error: variable or field ‘do_md5_game’ declared void
key2pb.c:63: error: ‘u8’ was not declared in this scope
key2pb.c:63: error: ‘gamename’ was not declared in this scope
key2pb.c:63: error: ‘u32’ was not declared in this scope
key2pb.c:63: error: ‘seed’ was not declared in this scope
key2pb.c:63: error: ‘u8’ was not declared in this scope
key2pb.c:63: error: ‘key’ was not declared in this scope
key2pb.c:63: error: initializer expression list treated as compound expression
key2pb.c:64: error: variable or field ‘do_md5’ declared void
key2pb.c:64: error: ‘u8’ was not declared in this scope
key2pb.c:64: error: ‘key’ was not declared in this scope
key2pb.c:64: error: ‘u32’ was not declared in this scope
key2pb.c:64: error: initializer expression list treated as compound expression
key2pb.c: In function ‘int main(int, char**)’:
key2pb.c:70: error: ‘u8’ was not declared in this scope
key2pb.c:70: error: ‘key1’ was not declared in this scope
key2pb.c:71: error: ‘key2’ was not declared in this scope
key2pb.c:72: error: ‘p1’ was not declared in this scope
key2pb.c:73: error: ‘p2’ was not declared in this scope
key2pb.c:74: error: ‘k’ was not declared in this scope
key2pb.c:118: error: ‘aa’ was not declared in this scope
key2pb.c:118: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:119: error: ‘bf1942’ was not declared in this scope
key2pb.c:119: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:120: error: ‘bf2’ was not declared in this scope
key2pb.c:120: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:121: error: ‘bf2142’ was not declared in this scope
key2pb.c:121: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:122: error: ‘bfv’ was not declared in this scope
key2pb.c:122: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:123: error: ‘cod’ was not declared in this scope
key2pb.c:123: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:124: error: ‘cod2’ was not declared in this scope
key2pb.c:124: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:125: error: ‘doom3’ was not declared in this scope
key2pb.c:125: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:126: error: ‘et’ was not declared in this scope
key2pb.c:126: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:127: error: ‘etqw’ was not declared in this scope
key2pb.c:127: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:128: error: ‘farcry’ was not declared in this scope
key2pb.c:128: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:129: error: ‘fear’ was not declared in this scope
key2pb.c:129: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:130: error: ‘mohpa’ was not declared in this scope
key2pb.c:130: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:131: error: ‘prey’ was not declared in this scope
key2pb.c:131: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:132: error: ‘quake3’ was not declared in this scope
key2pb.c:132: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:133: error: ‘quake4’ was not declared in this scope
key2pb.c:133: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:134: error: ‘r63’ was not declared in this scope
key2pb.c:134: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:135: error: ‘r64’ was not declared in this scope
key2pb.c:135: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:136: error: ‘r65’ was not declared in this scope
key2pb.c:136: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:137: error: ‘rtcw’ was not declared in this scope
key2pb.c:137: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:138: error: ‘sof2’ was not declared in this scope
key2pb.c:138: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:139: error: ‘scpt’ was not declared in this scope
key2pb.c:139: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:140: error: ‘uo’ was not declared in this scope
key2pb.c:140: error: ‘do_md5_game’ cannot be used as a function
key2pb.c:141: error: ‘warrock’ was not declared in this scope
key2pb.c:141: error: ‘do_md5_game’ cannot be used as a function
key2pb.c: At global scope:
key2pb.c:149: error: variable or field ‘do_md5_game’ declared void
key2pb.c:149: error: redefinition of ‘int do_md5_game’
key2pb.c:63: error: ‘int do_md5_game’ previously defined here
key2pb.c:149: error: ‘u8’ was not declared in this scope
key2pb.c:149: error: ‘gamename’ was not declared in this scope
key2pb.c:149: error: ‘u32’ was not declared in this scope
key2pb.c:149: error: ‘seed’ was not declared in this scope
key2pb.c:149: error: ‘u8’ was not declared in this scope
key2pb.c:149: error: ‘key’ was not declared in this scope
key2pb.c:161: error: variable or field ‘do_md5’ declared void
key2pb.c:161: error: redefinition of ‘int do_md5’
key2pb.c:64: error: ‘int do_md5’ previously defined here
key2pb.c:161: error: ‘u8’ was not declared in this scope
key2pb.c:161: error: ‘key’ was not declared in this scope
key2pb.c:161: error: ‘u32’ was not declared in this scope

```

---

### Post by lloyd_b on 2007-08-24
The vast majority of your errors are a result of a missing include file.  Try adding
```
#include <stdint.h>
```
with the other includes, and most of those errors disappear.

Lloyd B.

---

### Post by somafm on 2007-08-24
8-) Works great now with that line. Thanks

---

