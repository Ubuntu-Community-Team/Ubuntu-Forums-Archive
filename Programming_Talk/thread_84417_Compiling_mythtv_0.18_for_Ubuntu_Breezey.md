---
title: "Compiling mythtv 0.18 for Ubuntu Breezey"
date: 2005-10-31
forum: Programming Talk
---

### Post by Steve Quezadas on 2005-10-31
I am trying to compile mythtv on my ubuntu system. I am using gcc version 3.4.5 and libc 2.3.5 . My kernel is 2.6.12. I know a little C++, but not enough to debug what's going on. I checked google and the maillist archvies and couldn't find anything. Has anyone seen this problem? Can someone point me in the right direction of what is going on? Here is the report:

make[2]: Entering directory `/home/steve/mythtv-0.18/libs/libmythtv'
g++ -c -pipe -march=pentiumpro -Wall -W -O3 -Wall -Wno-switch -fomit-frame-pointer `freetype-config --cflags` -D_REENTRANT -DPIC -fPIC -DMMX -DUSING_IVTV -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr/local\" -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/local/include -I../.. -I../libmyth -I.. -Idvbdev -Impeg -I../libavcodec -I../libmythmpeg2 -I/usr/include/qt3 -o mpegstreamdata.o mpeg/mpegstreamdata.cpp
mpeg/mpegstreamdata.h:75: error: â€˜PESPacketâ€™ has not been declared
mpeg/mpegstreamdata.h:76: error: ISO C++ forbids declaration of â€˜PESPacketâ€™ with no type
mpeg/mpegstreamdata.h:76: error: expected â€˜;â€™ before â€˜*â€™ token
mpeg/mpegstreamdata.h:77: error: expected `;' before â€˜voidâ€™
mpeg/mpegstreamdata.h:101: error: â€˜PESPacketâ€™ was not declared in this scope
mpeg/mpegstreamdata.h:101: error: template argument 2 is invalid
mpeg/mpegstreamdata.h: In member function â€˜void MPEGStreamData::ClearPartialPES(unsigned int)â€™:
mpeg/mpegstreamdata.h:77: error: request for member â€˜removeâ€™ in â€˜((MPEGStreamData*)this)->MPEGStreamData::_partial_pes_packet_cacheâ€™, which is of non-class type â€˜intâ€™
mpeg/mpegstreamdata.h: At global scope:
mpeg/mpegstreamdata.h:106: error: prototype for â€˜void MPEGStreamData::SavePartialPES(unsigned int, PESPacket*)â€™ does not match any in class â€˜MPEGStreamDataâ€™
mpeg/mpegstreamdata.h:75: error: candidate is: void MPEGStreamData::SavePartialPES(unsigned int, int*)
mpeg/mpegstreamdata.h: In member function â€˜void MPEGStreamData::SavePartialPES(unsigned int, PESPacket*)â€™:
mpeg/mpegstreamdata.h:107: error: request for member â€˜findâ€™ in â€˜((MPEGStreamData*)this)->MPEGStreamData::_partial_pes_packet_cacheâ€™, which is of non-class type â€˜intâ€™
mpeg/mpegstreamdata.h:108: error: request for member â€˜endâ€™ in â€˜((MPEGStreamData*)this)->MPEGStreamData::_partial_pes_packet_cacheâ€™, which is of non-class type â€˜intâ€™
mpeg/mpegstreamdata.h:109: error: invalid types â€˜int[unsigned int]â€™ for array subscript
mpeg/mpegstreamdata.h:113: error: request for member â€˜replaceâ€™ in â€˜((MPEGStreamData*)this)->MPEGStreamData::_partial_pes_packet_cacheâ€™, which is of non-class type â€˜intâ€™
mpeg/mpegstreamdata.h: At global scope:
mpeg/mpegstreamdata.h:138: warning: unused parameter â€˜tspacketâ€™
mpeg/mpegstreamdata.cpp: In member function â€˜virtual void MPEGStreamData::Reset(int, int)â€™:
mpeg/mpegstreamdata.cpp:25: error: request for member â€˜clearâ€™ in â€˜((MPEGStreamData*)this)->MPEGStreamData::_partial_pes_packet_cacheâ€™, which is of non-class type â€˜intâ€™
mpeg/mpegstreamdata.cpp: In member function â€˜void MPEGStreamData::DeletePartialPES(unsigned int)â€™:
mpeg/mpegstreamdata.cpp:38: error: invalid types â€˜int[unsigned int]â€™ for array subscript
mpeg/mpegstreamdata.cpp: In member function â€˜PSIPTable* MPEGStreamData::AssemblePSIP(const TSPacket*)â€™:
mpeg/mpegstreamdata.cpp:68: error: â€˜GetPartialPESâ€™ was not declared in this scope
make[2]: *** [mpegstreamdata.o] Error 1
make[2]: Leaving directory `/home/steve/mythtv-0.18/libs/libmythtv'
make[1]: *** [sub-libmythtv] Error 2
make[1]: Leaving directory `/home/steve/mythtv-0.18/libs'
make: *** [sub-libs] Error 2



_______________________________________________
mythtv-users mailing list
[email]mythtv-users@mythtv.org[/email]
[http://mythtv.org/cgi-bin/mailman/listinfo/mythtv-users](http://mythtv.org/cgi-bin/mailman/listinfo/mythtv-users)

---

