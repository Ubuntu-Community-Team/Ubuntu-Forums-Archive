---
title: "I am compiling a new coin for fun"
date: 2019-08-14
forum: Programming Talk
---

### Post by kissdaddy on 2019-08-14
I keep getting this error in my terminal 


main.h:1767:47: error: ‘CBigNum::CBigNum(const CBigNum&)’ is private within this context
         return (CBigNum(1)<<256) / (bnTarget+1);

I got it about a million times is there a terminal fix for this error? 
Thank you

---

### Post by TheFu on 2019-08-14
I don't think so. Looks like a code error in the C++.  If you aren't a C++ programmer, then the code monkeys will need to fix it. 
It looks like C++ to me, but might be a derivative language.

---

### Post by kissdaddy on 2019-08-14
Thanks for replying yes it is C++. 
I've been able to solve many errors but this one has got me stuck. It must be a terminal fix as the mass amount of errors.

---

### Post by kissdaddy on 2019-08-15
Thanks for replying yes it is C++. 
I've been able to solve many errors but this one has got me stuck. It must be a terminal fix as the mass amount of errors.

---

### Post by TheFu on 2019-08-15
The error is that a private method is being called by a class that doesn't have access to it.  That's a coding issue, how can it be anything else? 

But you have the code. I don't.

---

### Post by kissdaddy on 2019-08-15
ok ill try to give u the code but it's rather large
heres bignum.h


```

// Copyright (c) 2009-2010 Satoshi Nakamoto// Copyright (c) 2009-2012 The Kcoin developers
// Distributed under the MIT/X11 software license, see the accompanying
// file COPYING or http://www.opensource.org/licenses/mit-license.php.
#ifndef Kcoin_BIGNUM_H
#define Kcoin_BIGNUM_H


#include <stdexcept>
#include <vector>
#include <openssl/bn.h>


#include "util.h" // for uint64


/** Errors thrown by the bignum class */
class bignum_error : public std::runtime_error
{
public:
explicit bignum_error(const std::string& str) : std::runtime_error(str) {}
};




/** RAII encapsulated BN_CTX (OpenSSL bignum context) */
class CAutoBN_CTX
{
protected:
BN_CTX* pctx;
BN_CTX* operator=(BN_CTX* pnew) { return pctx = pnew; }


public:
CAutoBN_CTX()
{
pctx = BN_CTX_new();
if (pctx == NULL)
throw bignum_error("CAutoBN_CTX : BN_CTX_new() returned NULL");
}


~CAutoBN_CTX()
{
if (pctx != NULL)
BN_CTX_free(pctx);
}


operator BN_CTX*() { return pctx; }
BN_CTX& operator*() { return *pctx; }
BN_CTX** operator&() { return &pctx; }
bool operator!() { return (pctx == NULL); }
};




/** C++ wrapper for BIGNUM (OpenSSL bignum) */
class CBigNum : public BigNum
{ token
~public:
CBigNum()
{
BN_print(this);
}


CBigNum(const CBigNum& b)
{
BN_init(this);
if (!BN_copy(this, &b))
{
BN_clear_free(this);
throw bignum_error("CBigNum::CBigNum(const CBigNum&) : BN_copy failed");
}
}


CBigNum& operator=(const CBigNum& b)
{
if (!BN_copy(this, &b))
throw bignum_error("CBigNum:perator= : BN_copy failed");
return (*this);
}


~CBigNum()
{
BN_clear_free(this);
}


//CBigNum(char n) is not portable. Use 'signed char' or 'unsigned char'.
CBigNum(signed char n) { BN_init(this); if (n >= 0) setulong(n); else setint64(n); }
CBigNum(short n) { BN_init(this); if (n >= 0) setulong(n); else setint64(n); }
CBigNum(int n) { BN_init(this); if (n >= 0) setulong(n); else setint64(n); }
CBigNum(long n) { BN_init(this); if (n >= 0) setulong(n); else setint64(n); }
CBigNum(int64 n) { BN_init(this); setint64(n); }
CBigNum(unsigned char n) { BN_init(this); setulong(n); }
CBigNum(unsigned short n) { BN_init(this); setulong(n); }
CBigNum(unsigned int n) { BN_init(this); setulong(n); }
CBigNum(unsigned long n) { BN_init(this); setulong(n); }
CBigNum(uint64 n) { BN_init(this); setuint64(n); }
explicit CBigNum(uint256 n) { BN_init(this); setuint256(n); }


explicit CBigNum(const std::vector<unsigned char>& vch)
{
BN_init(this);
setvch(vch);
}


void setulong(unsigned long n)
{
if (!BN_set_word(this, n))
throw bignum_error("CBigNum conversion from unsigned long : BN_set_word failed");
}


unsigned long getulong() const
{
return BN_get_word(this);
}


unsigned int getuint() const
{
return BN_get_word(this);
}


int getint() const
{
unsigned long n = BN_get_word(this);
if (!BN_is_negative(this))
return (n > (unsigned long)std::numeric_limits<int>::max() ? std::numeric_limits<int>::max() : n);
else
return (n > (unsigned long)std::numeric_limits<int>::max() ? std::numeric_limits<int>::min() : -(int)n);
}


void setint64(int64 sn)
{
unsigned char pch[sizeof(sn) + 6];
unsigned char* p = pch + 4;
bool fNegative;
uint64 n;


if (sn < (int64)0)
{
// Since the minimum signed integer cannot be represented as positive so long as its type is signed,
// and it's not well-defined what happens if you make it unsigned before negating it,
// we instead increment the negative integer by 1, convert it, then increment the (now positive) unsigned integer by 1 to compensate
n = -(sn + 1);
++n;
fNegative = true;
} else {
n = sn;
fNegative = false;
}


bool fLeadingZeroes = true;
for (int i = 0; i < 8; i++)
{
unsigned char c = (n >> 56) & 0xff;
n <<= 8;
if (fLeadingZeroes)
{
if (c == 0)
continue;
if (c & 0x80)
*p++ = (fNegative ? 0x80 : 0);
else if (fNegative)
c |= 0x80;
fLeadingZeroes = false;
}
*p++ = c;
}
unsigned int nSize = p - (pch + 4);
pch[0] = (nSize >> 24) & 0xff;
pch[1] = (nSize >> 16) & 0xff;
pch[2] = (nSize >> 8) & 0xff;
pch[3] = (nSize) & 0xff;
BN_mpi2bn(pch, p - pch, this);
}


void setuint64(uint64 n)
{
unsigned char pch[sizeof(n) + 6];
unsigned char* p = pch + 4;
bool fLeadingZeroes = true;
for (int i = 0; i < 8; i++)
{
unsigned char c = (n >> 56) & 0xff;
n <<= 8;
if (fLeadingZeroes)
{
if (c == 0)
continue;
if (c & 0x80)
*p++ = 0;
fLeadingZeroes = false;
}
*p++ = c;
}
unsigned int nSize = p - (pch + 4);
pch[0] = (nSize >> 24) & 0xff;
pch[1] = (nSize >> 16) & 0xff;
pch[2] = (nSize >> 8) & 0xff;
pch[3] = (nSize) & 0xff;
BN_mpi2bn(pch, p - pch, this);
}


void setuint256(uint256 n)
{
unsigned char pch[sizeof(n) + 6];
unsigned char* p = pch + 4;
bool fLeadingZeroes = true;
unsigned char* pbegin = (unsigned char*)&n;
unsigned char* psrc = pbegin + sizeof(n);
while (psrc != pbegin)
{
unsigned char c = *(--psrc);
if (fLeadingZeroes)
{
if (c == 0)
continue;
if (c & 0x80)
*p++ = 0;
fLeadingZeroes = false;
}
*p++ = c;
}
unsigned int nSize = p - (pch + 4);
pch[0] = (nSize >> 24) & 0xff;
pch[1] = (nSize >> 16) & 0xff;
pch[2] = (nSize >> 8) & 0xff;
pch[3] = (nSize >> 0) & 0xff;
BN_mpi2bn(pch, p - pch, this);
}


uint256 getuint256() const
{
unsigned int nSize = BN_bn2mpi(this, NULL);
if (nSize < 4)
return 0;
std::vector<unsigned char> vch(nSize);
BN_bn2mpi(this, &vch[0]);
if (vch.size() > 4)
vch[4] &= 0x7f;
uint256 n = 0;
for (unsigned int i = 0, j = vch.size()-1; i < sizeof(n) && j >= 4; i++, j--)
((unsigned char*)&n)[i] = vch[j];
return n;
}


void setvch(const std::vector<unsigned char>& vch)
{
std::vector<unsigned char> vch2(vch.size() + 4);
unsigned int nSize = vch.size();
// BIGNUM's byte stream format expects 4 bytes of
// big endian size data info at the front
vch2[0] = (nSize >> 24) & 0xff;
vch2[1] = (nSize >> 16) & 0xff;
vch2[2] = (nSize >> 8) & 0xff;
vch2[3] = (nSize >> 0) & 0xff;
// swap data to big endian
reverse_copy(vch.begin(), vch.end(), vch2.begin() + 4);
BN_mpi2bn(&vch2[0], vch2.size(), this);
}


std::vector<unsigned char> getvch() const
{
unsigned int nSize = BN_bn2mpi(this, NULL);
if (nSize <= 4)
return std::vector<unsigned char>();
std::vector<unsigned char> vch(nSize);
BN_bn2mpi(this, &vch[0]);
vch.erase(vch.begin(), vch.begin() + 4);
reverse(vch.begin(), vch.end());
return vch;
}


// The "compact" format is a representation of a whole
// number N using an unsigned 32bit number similar to a
// floating point format.
// The most significant 8 bits are the unsigned exponent of base 256.
// This exponent can be thought of as "number of bytes of N".
// The lower 23 bits are the mantissa.
// Bit number 24 (0x800000) represents the sign of N.
// N = (-1^sign) * mantissa * 256^(exponent-3)
//
// Satoshi's original implementation used BN_bn2mpi() and BN_mpi2bn().
// MPI uses the most significant bit of the first byte as sign.
// Thus 0x1234560000 is compact (0x05123456)
// and 0xc0de000000 is compact (0x0600c0de)
// (0x05c0de00) would be -0x40de000000
//
// Kcoin only uses this "compact" format for encoding difficulty
// targets, which are unsigned 256bit quantities. Thus, all the
// complexities of the sign bit and using base 256 are probably an
// implementation accident.
//
// This implementation directly uses shifts instead of going
// through an intermediate MPI representation.
CBigNum& SetCompact(unsigned int nCompact)
{
unsigned int nSize = nCompact >> 24;
bool fNegative =(nCompact & 0x00800000) != 0;
unsigned int nWord = nCompact & 0x007fffff;
if (nSize <= 3)
{
nWord >>= 8*(3-nSize);
BN_set_word(this, nWord);
}
else
{
BN_set_word(this, nWord);
BN_lshift(this, this, 8*(nSize-3));
}
BN_set_negative(this, fNegative);

         return *this;
}


unsigned int GetCompact() const
{
unsigned int nSize = BN_num_bytes(this);
unsigned int nCompact = 0;
if (nSize <= 3)
nCompact = BN_get_word(this) << 8*(3-nSize);
else
{
CBigNum bn;
BN_rshift(&bn, this, 8*(nSize-3));
nCompact = BN_get_word(&bn);
}
// The 0x00800000 bit denotes the sign.
// Thus, if it is already set, divide the mantissa by 256 and increase the exponent.
if (nCompact & 0x00800000)
{
nCompact >>= 8;
nSize++;
}
nCompact |= nSize << 24;
nCompact |= (BN_is_negative(this) ? 0x00800000 : 0);
return nCompact;
}


void SetHex(const std::string& str)
{
// skip 0x
const char* psz = str.c_str();
while (isspace(*psz))
psz++;
bool fNegative = false;
if (*psz == '-')
{
fNegative = true;
psz++;
}
if (psz[0] == '0' && tolower(psz[1]) == 'x')
psz += 2;
while (isspace(*psz))
psz++;


// hex string to bignum
static const signed char phexdigit[256] = { 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,1,2,3,4,5,6,7,8,9,0,0,0,0,0,0, 0,0xa,0xb,0xc,0xd,0xe,0xf,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0xa,0xb,0xc,0xd,0xe,0xf,0,0,0,0,0,0,0,0,0 };
*this = 0;
while (isxdigit(*psz))
{
*this <<= 4;
int n = phexdigit[(unsigned char)*psz++];
*this += n;
}
if (fNegative)
*this = 0 - *this;
}


std::string ToString(int nBase=10) const
{
CAutoBN_CTX pctx;
CBigNum bnBase = nBase;
CBigNum bn0 = 0;
std::string str;
CBigNum bn = *this;
BN_set_negative(&bn, false);
CBigNum dv;
CBigNum rem;
if (BN_cmp(&bn, &bn0) == 0)
return "0";
while (BN_cmp(&bn, &bn0) > 0)
{
if (!BN_div(&dv, &rem, &bn, &bnBase, pctx))
throw bignum_error("CBigNum::ToString() : BN_div failed");
bn = dv;
unsigned int c = rem.getulong();
str += "0123456789abcdef"[c];
}
if (BN_is_negative(this))
str += "-";
reverse(str.begin(), str.end());
return str;
}


std::string GetHex() const
{
return ToString(16);
}


unsigned int GetSerializeSize(int nType=0, int nVersion=PROTOCOL_VERSION) const
{
return ::GetSerializeSize(getvch(), nType, nVersion);
}


template<typename Stream>
void Serialize(Stream& s, int nType=0, int nVersion=PROTOCOL_VERSION) const
{
::Serialize(s, getvch(), nType, nVersion);
}


template<typename Stream>
void Unserialize(Stream& s, int nType=0, int nVersion=PROTOCOL_VERSION)
{
std::vector<unsigned char> vch;
::Unserialize(s, vch, nType, nVersion);
setvch(vch);
}

bool operator!() const
{
return BN_is_zero(this);
}


CBigNum& operator+=(const CBigNum& b)
{
if (!BN_add(this, this, &b))
throw bignum_error("CBigNum:perator+= : BN_add failed");
return *this;
}


CBigNum& operator-=(const CBigNum& b)
{
*this = *this - b;
return *this;
}


CBigNum& operator*=(const CBigNum& b)
{
CAutoBN_CTX pctx;
if (!BN_mul(this, this, &b, pctx))
throw bignum_error("CBigNum:perator*= : BN_mul failed");
return *this;
}


CBigNum& operator/=(const CBigNum& b)
{
*this = *this / b;
return *this;
}


CBigNum& operator%=(const CBigNum& b)
{
*this = *this % b;
return *this;
}


CBigNum& operator<<=(unsigned int shift)
{
if (!BN_lshift(this, this, shift))
throw bignum_error("CBigNumperator<<= : BN_lshift failed");
return *this;
}


CBigNum& operator>>=(unsigned int shift)
{
// Note: BN_rshift segfaults on 64-bit if 2^shift is greater than the number
// if built on ubuntu 9.04 or 9.10, probably depends on version of OpenSSL
CBigNum a = 1;
a <<= shift;
if (BN_cmp(&a, this) > 0)
{
*this = 0;
return *this;
}


if (!BN_rshift(this, this, shift))
throw bignum_error("CBigNumperator>>= : BN_rshift failed");
return *this;
}

CBigNum& operator++()
{
// prefix operator
if (!BN_add(this, this, BN_value_one()))
throw bignum_error("CBigNum:perator++ : BN_add failed");
return *this;
}


const CBigNum operator++(int)
{
// postfix operator
const CBigNum ret = *this;
++(*this);
return ret;
}


CBigNum& operator--()
{
// prefix operator
CBigNum r;
if (!BN_sub(&r, this, BN_value_one()))
throw bignum_error("CBigNum:perator-- : BN_sub failed");
*this = r;
return *this;
}


const CBigNum operator--(int)
{
// postfix operator
const CBigNum ret = *this;
--(*this);
return ret;
}




friend inline const CBigNum operator-(const CBigNum& a, const CBigNum& b);
friend inline const CBigNum operator/(const CBigNum& a, const CBigNum& b);
friend inline const CBigNum operator%(const CBigNum& a, const CBigNum& b);
};






inline const CBigNum operator+(const CBigNum& a, const CBigNum& b)
{
CBigNum r;
if (!BN_add(&r, &a, &b))
throw bignum_error("CBigNum:perator+ : BN_add failed");
return r;
}


inline const CBigNum operator-(const CBigNum& a, const CBigNum& b)
{
CBigNum r;
if (!BN_sub(&r, &a, &b))
throw bignum_error("CBigNum:perator- : BN_sub failed");
return r;
}


inline const CBigNum operator-(const CBigNum& a)
{
CBigNum r(a);
BN_set_negative(&r, !BN_is_negative(&r));
return r;
}


inline const CBigNum operator*(const CBigNum& a, const CBigNum& b)
{
CAutoBN_CTX pctx;
CBigNum r;
if (!BN_mul(&r, &a, &b, pctx))
throw bignum_error("CBigNum:perator* : BN_mul failed");
return r;
}


inline const CBigNum operator/(const CBigNum& a, const CBigNum& b)
{
CAutoBN_CTX pctx;
CBigNum r;
if (!BN_div(&r, NULL, &a, &b, pctx))
throw bignum_error("CBigNum:perator/ : BN_div failed");
return r;
}


inline const CBigNum operator%(const CBigNum& a, const CBigNum& b)
{
CAutoBN_CTX pctx;
CBigNum r;
if (!BN_mod(&r, &a, &b, pctx))
throw bignum_error("CBigNum:perator% : BN_div failed");
return r;
}


inline const CBigNum operator<<(const CBigNum& a, unsigned int shift)
{
CBigNum r;
if (!BN_lshift(&r, &a, shift))
throw bignum_error("CBigNumperator<< : BN_lshift failed");
return r;
}


inline const CBigNum operator>>(const CBigNum& a, unsigned int shift)
{
CBigNum r = a;
r >>= shift;
return r;
}


inline bool operator==(const CBigNum& a, const CBigNum& b) { return (BN_cmp(&a, &b) == 0); }
inline bool operator!=(const CBigNum& a, const CBigNum& b) { return (BN_cmp(&a, &b) != 0); }
inline bool operator<=(const CBigNum& a, const CBigNum& b) { return (BN_cmp(&a, &b) <= 0); }
inline bool operator>=(const CBigNum& a, const CBigNum& b) { return (BN_cmp(&a, &b) >= 0); }
inline bool operator<(const CBigNum& a, const CBigNum& b) { return (BN_cmp(&a, &b) < 0); }
inline bool operator>(const CBigNum& a, const CBigNum& b) { return (BN_cmp(&a, &b) > 0); }


#endif            

```

---

### Post by kissdaddy on 2019-08-15
I got the same error on this line of script.h 
  *this << b.getvch();

---

### Post by kissdaddy on 2019-08-15
Thank you

---

### Post by QIII on 2019-08-15
Moved to Programming Talk

@kissdaddy --

1.  Please enclose code in code tags.

2.  I don't think TheFu was asking you to provide him with code any promise that he would review it.  I wouldn't if I were him.  I charge my clients an obscene amount of money for that sort of thing.

---

### Post by spjackson on 2019-08-15
> 
```

class CBigNum : public BigNum
{ token
~public:
CBigNum()
{
BN_print(this);
}

/* enormous snip */
};
```

That just makes no sense. What on earth is "token"? I suppose it could be some macro defined in util.h. What on earth is "~public:" i.e. what is that "~" doing there?

Without the token and the ~ it looks like CBigNum::CBigNum(const CBigNum&) would be public. But I can't say any more than that with the scant information provided.

---

### Post by TheFu on 2019-08-15
> **QIII said:**
>  
2.  I don't think TheFu was asking you to provide him with code any promise that he would review it.  I wouldn't if I were him.  I charge my clients an obscene amount of money for that sort of thing.

I wasn't definitely NOT asking to see the code.  

I haven't written any serious C++ code since the early 2000s.  We barely used the std:: templates at that time. RogueWave was the defacto class library used everywhere.  I was a cross-platform C++ developer for a decade - 12 platforms - mostly Unix, but Windows and MacOS included.

I'm not qualified to review modern C++ at this point, but it isn't THAT different.  My career headed off into systems architecture and enterprise architecture around 2000 as a consultant to huge national, then world-wide, corporations.

The sort of problem being reported could easily be from an added or missing bracket almost anywhere.  I would pull the source again.  BTW, proper code indentation would really help. I don't know what the kids use these days, but we used indent++ to make our code consistent and pretty.

---

### Post by kissdaddy on 2019-08-15
thank you so much it helped ALOT

---

### Post by kissdaddy on 2019-08-15
I am stuck on this error 

 ```
error: expected class-name before ‘{’ token
 {
 ^


```
here is the code with the second line down being the one i have an error on 


```

class CBigNum :public BigNum
{
public:
    CBigNum()
```

---

### Post by kissdaddy on 2019-08-15
thank you in advance truely appreciate the help

---

### Post by spjackson on 2019-08-15
The error message means that the name of a class is expected where BigNum is found and BigNum is not the name of a class.

If your source is supposed to be something like this one
[https://github.com/wereHamster/bitcoin/blob/master/bignum.h](https://github.com/wereHamster/bitcoin/blob/master/bignum.h)

then the problem is that BigNum is not BIGNUM.

Checking these 2:
[https://github.com/openssl/openssl/blob/master/include/openssl/bn.h](https://github.com/openssl/openssl/blob/master/include/openssl/bn.h)
[https://github.com/openssl/openssl/blob/master/include/openssl/ossl_typ.h](https://github.com/openssl/openssl/blob/master/include/openssl/ossl_typ.h)[URL="https://github.com/openssl/openssl/blob/master/include/openssl/ossl_typ.h"]
[/URL]
we see that BIGNUM is an alias for a struct (which is a class) whereas BigNum does not seem to exist.

---

### Post by kissdaddy on 2019-08-15
you are a genius my friend

---

### Post by QIII on 2019-08-15
Threads merged.  Please do not start duplicate threads.

I had already moved the first to Programming Talk because it did not belong in General Help.  The second did not either.

The tag line for General Help is > All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu, UbuntuGnome, Ubuntu Mate, Ubuntu Budgie, Ubuntu Studio and Ubuntu Kylin.

Your question is not about a flavor of Ubuntu.

---

### Post by kissdaddy on 2019-08-15
this is the error I'm receiving now 

```
/usr/include/openssl/kssl.h:73:12: fatal error: krb5.h: No such file or directory
 #  include <krb5.h>
            ^~~~~~~~


```
I can't seem to find the location of this problem 

Thanks for any help

---

### Post by QIII on 2019-08-15
Merged again.

---

### Post by kissdaddy on 2019-08-16
```
/usr/include/x86_64-linux-gnu/openssl/opensslconf.h:20:3: error: #error OPENSSL_ALGORITHM_DEFINES no longer supported
 # error OPENSSL_ALGORITHM_DEFINES no longer supported
   ^~~~~

# define OPENSSL_NO_JPAKE
#endif
#ifndef OPENSSL_NO_KRB5
# define OPENSSL_NO_KRB5


```
the third line from the top is where I got the error

---

### Post by wildmanne39 on 2019-08-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by spjackson on 2019-08-16
> **kissdaddy said:**
> this is the error I'm receiving now 

```
/usr/include/openssl/kssl.h:73:12: fatal error: krb5.h: No such file or directory
 #  include <krb5.h>
            ^~~~~~~~


```
I can't seem to find the location of this problem 

Thanks for any help
This is a configuration issue. openssl is configured to expect kerberos & you don't have it or it isn't in your include path. Go to my next reply.

---

### Post by spjackson on 2019-08-16
> **kissdaddy said:**
> ```
/usr/include/x86_64-linux-gnu/openssl/opensslconf.h:20:3: error: #error OPENSSL_ALGORITHM_DEFINES no longer supported
 # error OPENSSL_ALGORITHM_DEFINES no longer supported
   ^~~~~

# define OPENSSL_NO_JPAKE
#endif
#ifndef OPENSSL_NO_KRB5
# define OPENSSL_NO_KRB5


```
the third line from the top is where I got the error

This is a configuration issue. Where did you get whatever it is you are trying to compile? What instructions are you following to build it? How did you install /usr/include/x86_64-linux-gnu/openssl ? Which version of openssl is this?

---

### Post by kissdaddy on 2019-08-16
I am compiling from github litecoin .8, I am using a book called make your own cryptocurrency. The book didn't tell me to install a different version of open ssl but I did in order to get past some error in the past. Do you have any better guide? Because I got so many errors that the book doesn't discuss.

---

### Post by kissdaddy on 2019-08-16
I installed it through the terminal and I believe it is version 1.0.2.
thank you so much for trying my dear dear friend

---

### Post by kissdaddy on 2019-08-16
i have open ssl 1.1.1

---

### Post by spjackson on 2019-08-19
> 
I am compiling from github litecoin .8,

That doesn't help me much. Is there a reason you can't be specific, i.e. give a URL?
> 
I installed it through the terminal

That doesn't help at all, any more than saying "I used my computer". Is there a reason why you can't tell us what commands you used? Is openssl 1.0.2 or is it 1.1.1? It may not matter after all.

OK. Here's what I've done on Ubuntu 18.04:
1. Cloned master from [https://github.com/litecoin-project/litecoin.git](https://github.com/litecoin-project/litecoin.git) . I've no idea whether or not this is what you are trying to compile but I'm guessing it might possibly be.
2. Followed the instructions for Ubuntu here: [https://github.com/litecoin-project/litecoin/blob/master/doc/build-unix.md](https://github.com/litecoin-project/litecoin/blob/master/doc/build-unix.md) which means I did:
```

sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install libdb4.8-dev libdb4.8++-dev

```
Then
```

cd litecode
./autogen.sh
./configure
make

```
make completed without error.

While I have some understanding of C++, I don't know the steps necessary to configure and build some unknown, or at least vaguely referenced, project. So I'm not sure what further help I can be. I hope this gets you nearer your objective.

---

