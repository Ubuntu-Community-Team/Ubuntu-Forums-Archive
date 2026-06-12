---
title: "SDL2 problem compiling 32 bit program"
date: 2016-03-03
forum: Packaging and Compiling Programs
---

### Post by adec2 on 2016-03-03
Hi, I'm trying to compile this program on a 64bit system


[https://github.com/zaps166/NFSIISE](https://github.com/zaps166/NFSIISE)


My problem is it cant find the SDL2 32bit library


Ive managed to find the required libGL library in the /usr/lib32/nvidia-361 folder but it just wont find SDL2


This is the install script:


    STRIP='-s'
fi


cd src || exit 1


echo -n " for"
if [[ $1 == "win32" ]]; then
    #Cross-compile for Window$
    echo -n " Window$... "
    i686-w64-mingw32-windres Windows/nfs2se.rc icon.o &&
    i686-w64-mingw32-gcc -Wall $C_FLAGS $CPU_FLAGS -c *.c &&
    yasm -f win32 NFS2SE.asm -o NFS2SE.o $DEBUG_ASM --prefix=_ &&
    yasm -f win32 EAcsnd.asm -o EAcsnd.asm.o $DEBUG_ASM --prefix=_ &&
    i686-w64-mingw32-ld --enable-stdcall-fixup -o "../Need For Speed II SE/nfs2se.exe" *.o --stack=0x7D00,0x7D00 --heap=0x2000,0x1000 -lws2_32 -lwinmm -lkernel32 -lmsvcrt -lopengl32 -lSDL2 -subsystem=$WIN_SUBSYSTEM $STRIP -e _start &&
    rm -f *.o &&
    echo "OK!"
else
    #Compile for Linux
    echo -n " Linux... "


    #32bit libraries for Linux
    LIB32_DIR=/usr/lib
    if [[ -d /usr/lib32 ]]; then
        LIB32_DIR=/usr/lib32
    fi


    gcc -Wall -m32 $C_FLAGS $CPU_FLAGS -c *.c &&
    yasm -f elf32 NFS2SE.asm -o NFS2SE.o $DEBUG_ASM &&
    yasm -f elf32 EAcsnd.asm -o EAcsnd.asm.o $DEBUG_ASM &&
    ld -m elf_i386 -dynamic-linker /lib/ld-linux.so.2 -o "../Need For Speed II SE/nfs2se" *.o -L$LIB32_DIR -lc -lSDL2 -lGL $STRIP -rpath=\$ORIGIN -e start &&
    rm -f *.o &&
    echo "OK!"
fi


Now when i do try to install libSDL2:i386 it does find it but it wants to delete other 64bit libraries before doing it which i really dont want to do


This is the error when trying to compile:


Building release for Linux... FetchTrackRecords.c: In function &#8216;fetchTrackRecords&#8217;:
FetchTrackRecords.c:53:9: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result [-Wunused-result]
    fgets(buffer, 80, f);
         ^
FetchTrackRecords.c:54:10: warning: ignoring return value of &#8216;fscanf&#8217;, declared with attribute warn_unused_result [-Wunused-result]
    fscanf(f, "%d\n", (int32_t *)buffer);
          ^
FetchTrackRecords.c:55:9: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result [-Wunused-result]
    fgets(buffer, 80, f);
         ^
FetchTrackRecords.c:61:10: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result [-Wunused-result]
     fgets(buffer, 80, f); //Skip unneeded line
          ^
FetchTrackRecords.c: In function &#8216;readEntry&#8217;:
FetchTrackRecords.c:31:7: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result [-Wunused-result]
  fgets(stfEntry->name, sizeof stfEntry->name, f);
       ^
FetchTrackRecords.c:35:8: warning: ignoring return value of &#8216;fscanf&#8217;, declared with attribute warn_unused_result [-Wunused-result]
  fscanf(f, "%hi\n%d\n%d\n", &stfEntry->car, &stfEntry->time, &stfEntry->mode);
        ^
Kernel32.c: In function &#8216;MapViewOfFile_wrap&#8217;:
Kernel32.c:466:7: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result [-Wunused-result]
   read(fMapping->fd, fileMap, size);
       ^
ld: cannot find -lSDL2


help much appreciated

---

