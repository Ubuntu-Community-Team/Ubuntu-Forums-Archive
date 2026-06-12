---
title: "Error with libserial"
date: 2015-10-26
forum: Programming Talk
---

### Post by mfvpcrec on 2015-10-26
Hello people :) , i have a question , i was compiling a program  with the libserial library , and i had this error

```

undefined reference to `SerialPort::SerialPort(std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'

```

I though "Well maybe i did not link the libserial library" but it was not. So i made a small program to test libserial like this

```

#include <iostream>
#include <SerialPort.h> 

using namespace  std;

int main (void)
{
    SerialPort  *serie= new SerialPort("A");
}

```

I compile with 

```

g++ program.cpp -lserial

```

And i had the same error.

The error appeared when I switched from Kubuntu 15.04 to Kubuntu 15.10 and when i use the constructor of SerialPort. I installed the old version of libserial but the error still appearing, maybe i forgot install something. Someone knows what is happening?

---

### Post by Rocket2DMn on 2015-10-28
Do you have the libserial headers installed on your system?  If you got libserial from the Ubuntu repos, you probably need to install libserial-dev as well.

---

### Post by mfvpcrec on 2015-10-28
Yes i installed libserialport0 libserial0 libserial-dev and libserial-dev and libserialport-dev.
The error happens when g++ tried to link the libserial library. Is like the constructor was never declared in the compiled library

---

### Post by Rocket2DMn on 2015-10-28
Hmm, I tried and get the same error.  Here's what I see on the objdump for the shared object:
```

$ objdump -T /usr/lib/x86_64-linux-gnu/libserial.so | grep text | grep SerialPort
0000000000009ed0 g    DF .text	0000000000000009  Base        _ZNK10SerialPort6IsOpenEv
000000000000ba90 g    DF .text	00000000000001b2  Base        _ZN10SerialPort9WriteByteEh
000000000000e910  w   DF .text	0000000000000020  Base        _ZN10SerialPort7NotOpenD0Ev
000000000000e950  w   DF .text	0000000000000020  Base        _ZN10SerialPort11AlreadyOpenD0Ev
000000000000b290 g    DF .text	00000000000005e1  Base        _ZN10SerialPort4OpenENS_8BaudRateENS_13CharacterSizeENS_6ParityENS_8StopBitsENS_11FlowControlE
000000000000e9d0  w   DF .text	0000000000000020  Base        _ZN10SerialPort19UnsupportedBaudRateD0Ev
000000000000d280 g    DF .text	0000000000000596  Base        _ZN10SerialPort8ReadLineEjc
000000000000e9f0  w   DF .text	0000000000000013  Base        _ZN10SerialPort11ReadTimeoutD2Ev
000000000000ccd0 g    DF .text	00000000000005a6  Base        _ZN10SerialPortC2ERKSs
0000000000009fa0 g    DF .text	00000000000002b0  Base        _ZN10SerialPort11SetBaudRateENS_8BaudRateE
000000000000d820 g    DF .text	00000000000004a2  Base        _ZN10SerialPort8ReadByteEj
000000000000e970  w   DF .text	0000000000000013  Base        _ZN10SerialPort10OpenFailedD2Ev
000000000000abe0 g    DF .text	0000000000000288  Base        _ZN10SerialPort16SetNumOfStopBitsENS_8StopBitsE
000000000000cb00 g    DF .text	00000000000001a9  Base        _ZN10SerialPortD2Ev
000000000000b880 g    DF .text	000000000000017b  Base        _ZNK10SerialPort14GetFlowControlEv
000000000000ebc0  w   DF .text	0000000000000130  Base        _ZN10SerialPort14SerialPortImplD0Ev
000000000000e8f0  w   DF .text	0000000000000013  Base        _ZN10SerialPort7NotOpenD1Ev
000000000000e930  w   DF .text	0000000000000013  Base        _ZN10SerialPort11AlreadyOpenD1Ev
000000000000c750 g    DF .text	00000000000001a0  Base        _ZNK10SerialPort6GetCtsEv
000000000000a3d0 g    DF .text	0000000000000225  Base        _ZN10SerialPort11SetCharSizeENS_13CharacterSizeE
000000000000efc0  w   DF .text	0000000000000908  Base        _ZN10SerialPort14SerialPortImpl17HandlePosixSignalEi
000000000000ae70 g    DF .text	0000000000000179  Base        _ZNK10SerialPort16GetNumOfStopBitsEv
000000000000c3f0 g    DF .text	00000000000001b7  Base        _ZN10SerialPort6SetRtsEb
000000000000e9b0  w   DF .text	0000000000000013  Base        _ZN10SerialPort19UnsupportedBaudRateD1Ev
000000000000bee0 g    DF .text	00000000000001a5  Base        _ZN10SerialPort5WriteERKSs
000000000000a780 g    DF .text	00000000000002be  Base        _ZN10SerialPort9SetParityENS_6ParityE
000000000000c090 g    DF .text	00000000000001b7  Base        _ZN10SerialPort6SetDtrEb
000000000000ea10  w   DF .text	0000000000000020  Base        _ZN10SerialPort11ReadTimeoutD0Ev
000000000000c8f0 g    DF .text	00000000000001a0  Base        _ZNK10SerialPort6GetDsrEv
000000000000e990  w   DF .text	0000000000000020  Base        _ZN10SerialPort10OpenFailedD0Ev
000000000000dcd0 g    DF .text	0000000000000c09  Base        _ZN10SerialPort4ReadERSt6vectorIhSaIhEEjj
000000000000ccb0 g    DF .text	0000000000000012  Base        _ZN10SerialPortD0Ev
000000000000ea90  w   DF .text	0000000000000130  Base        _ZN10SerialPort14SerialPortImplD1Ev
000000000000e8f0  w   DF .text	0000000000000013  Base        _ZN10SerialPort7NotOpenD2Ev
000000000000e930  w   DF .text	0000000000000013  Base        _ZN10SerialPort11AlreadyOpenD2Ev
000000000000aff0 g    DF .text	0000000000000293  Base        _ZN10SerialPort14SetFlowControlENS_11FlowControlE
000000000000ca90 g    DF .text	0000000000000064  Base        _ZNK10SerialPort17GetFileDescriptorEv
0000000000009ee0 g    DF .text	00000000000000bc  Base        _ZN10SerialPort5CloseEv
000000000000ccd0 g    DF .text	00000000000005a6  Base        _ZN10SerialPortC1ERKSs
000000000000bc50 g    DF .text	0000000000000290  Base        _ZN10SerialPort5WriteERKSt6vectorIhSaIhEE
000000000000e9b0  w   DF .text	0000000000000013  Base        _ZN10SerialPort19UnsupportedBaudRateD2Ev
000000000000ba00 g    DF .text	000000000000008f  Base        _ZNK10SerialPort15IsDataAvailableEv
000000000000aa40 g    DF .text	0000000000000194  Base        _ZNK10SerialPort9GetParityEv
000000000000c5b0 g    DF .text	00000000000001a0  Base        _ZNK10SerialPort6GetRtsEv
000000000000e9f0  w   DF .text	0000000000000013  Base        _ZN10SerialPort11ReadTimeoutD1Ev
000000000000a600 g    DF .text	0000000000000176  Base        _ZNK10SerialPort11GetCharSizeEv
000000000000c250 g    DF .text	000000000000019f  Base        _ZNK10SerialPort6GetDtrEv
000000000000a250 g    DF .text	000000000000017b  Base        _ZNK10SerialPort11GetBaudRateEv
000000000000e970  w   DF .text	0000000000000013  Base        _ZN10SerialPort10OpenFailedD1Ev
000000000000ea90  w   DF .text	0000000000000130  Base        _ZN10SerialPort14SerialPortImplD2Ev
000000000000cb00 g    DF .text	00000000000001a9  Base        _ZN10SerialPortD1Ev

```

I don't check that often, but I don't see a straight-up *SerialPort* listed, and I'm not sure what's up with the _ZN prefixes (but maybe they're ok?).

---

### Post by mfvpcrec on 2015-10-28
Well...so that is a problem of ubuntu package... I guess that i must downgrade my version of ubuntu... :(
It was very awesome the objdump i didn't know do that

Thank you.
Bye!

---

### Post by spjackson on 2015-10-29
> **mfvpcrec said:**
> Well...so that is a problem of ubuntu package... I guess that i must downgrade my version of ubuntu... :(

I'd be surprised if the issue is limited to libserial. The bigger issue is the C++ ABI change between g++ 4 and g++ 5. Your sample does build on 15.10 with:

```

g++ program.cpp -lserial -lpthread -D_GLIBCXX_USE_CXX11_ABI=0

```
I'm not sure if there's a better "official" answer.

---

