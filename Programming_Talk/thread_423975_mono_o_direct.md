---
title: "mono o_direct"
date: 2007-04-26
forum: Programming Talk
---

### Post by cdenley on 2007-04-26
I'm writing a C# program that writes data to multiple drives simultaneously.  Using a regular BinaryWriter makes my program and the entire system run slow. Would using a Unix stream with the O_DIRECT flag be more efficient. If so, how do I make this work?

Here is a simple example of what I'm trying to do:
```
using System;
using System.IO;
using Mono.Unix;
using Mono.Unix.Native;

namespace test
{
	class MainClass
	{
		public static void Main(string[] args)
		{
			int bufferSize=(int)Syscall.sysconf(SysconfName._SC_PAGESIZE);
			FileStream fs=new FileStream("data.img",FileMode.Open,FileAccess.Read);
			BinaryReader br=new BinaryReader(fs);
			int fd=Syscall.open("/dev/sdc",OpenFlags.O_WRONLY|OpenFlags.O_DIRECT);
			UnixStream us=new UnixStream(fd);
			byte[] buffer=br.ReadBytes(bufferSize);
			while(buffer.Length>0)
			{
				us.Write(buffer,0,buffer.Length);
				buffer=br.ReadBytes(bufferSize);
			}
			us.Close();
			br.Close();
		}
	}
}
```

The error I get is:
```
Unhandled Exception: System.ArgumentException: Invalid argument ---> Mono.Unix.UnixIOException: Invalid argument [EINVAL].--- End of inner exception stack trace ---

  at Mono.Unix.UnixMarshal.ThrowExceptionForLastError () [0x00000] in /build/buildd/mono-1.2.3.1/mcs/class/Mono.Posix/Mono.Unix/UnixMarshal.cs:456 
  at Mono.Unix.UnixStream.Write (System.Byte[] buffer, Int32 offset, Int32 count) [0x00056] in /build/buildd/mono-1.2.3.1/mcs/class/Mono.Posix/Mono.Unix/UnixStream.cs:299 
  at test.MainClass.Main (System.String[] args) [0x00043] in /home/cdenley/test/test/Main.cs:21 
```

If I remove the O_DIRECT flag, the code works.

---

### Post by cdenley on 2007-04-27
I figured it out. When writing to a file with the O_DIRECT flag, the memory location and length of the buffer must be a multiple of the memory page size (4096 bytes). I'm guessing that the UnixStream class doesn't check if the file was opened using the O_DIRECT flag, and even though I use a valid buffer size, the buffer location in memory is probably random. The only solution, I believe, is to use system calls. I will probably write my own file stream class, implement it in my application, then hopefully it will perform as expected.

my revised simplified example:
```
using System;
using Mono.Unix.Native;

namespace test
{
	class MainClass
	{
		public static void Main(string[] args)
		{
			int fdin=Syscall.open("data.img",OpenFlags.O_RDONLY|OpenFlags.O_SYNC|OpenFlags.O_LARGEFILE|OpenFlags.O_DIRECT);
			int fdout=Syscall.open("/dev/sdc",OpenFlags.O_WRONLY|OpenFlags.O_CREAT|OpenFlags.O_SYNC|OpenFlags.O_LARGEFILE|OpenFlags.O_DIRECT);
			Stat statin;
			Syscall.fstat(fdin,out statin);
			long pageSize=Syscall.sysconf(SysconfName._SC_PAGESIZE);
			ulong bufferSize=(ulong)pageSize*4;
			long memSize=pageSize*5;
			IntPtr mem=Syscall.malloc((ulong)memSize);
			long diff=pageSize-(mem.ToInt64()%pageSize);
			IntPtr buffer=(IntPtr)(mem.ToInt64()+diff);
			for(long i=0;i<statin.st_size;i+=pageSize)
			{		
				Syscall.lseek(fdin,i,SeekFlags.SEEK_SET);
				Syscall.read(fdin,buffer,bufferSize);
				Syscall.lseek(fdout,i,SeekFlags.SEEK_SET);
				Syscall.write(fdout,buffer,bufferSize);
			}
			Syscall.free(mem);
			Syscall.ftruncate(fdout,statin.st_size);
			Syscall.close(fdout);
			Syscall.close(fdin);
		}
	}
}
```

---

