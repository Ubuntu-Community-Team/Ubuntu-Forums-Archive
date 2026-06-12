---
title: "Segmentation fault (core dumped)"
date: 2013-07-09
forum: Programming Talk
---

### Post by priyaanand on 2013-07-09
I have a code where in I use zlib with objetive-c.When I complie my code I get this error.

"2013-07-09 12:53:19.607 practicemain[3465] 0
Segmentation fault (core dumped)"

What could be the problem?

TIA

---

### Post by oldos2er on 2013-07-09
Post moved to its own thread.

---

### Post by r-senior on 2013-07-09
You've tried to access memory that you don't have the right to access. In Objective-C, this is often the result of accessing an object that has been deallocated but there are other reasons.

What version of Objective-C are you writing? Are you using modern Objective-C/ARC, i.e. Apple stuff? Can you post your code? (In code tags please).

---

### Post by priyaanand on 2013-07-09
Thank You r-senior, for the reply.I'm using objective -C ,the Apple stuff.My goal is to compress and decompress xlsx files in objective-C only using zlib.I have not found any clear example as in how to use zlib.I anyway tried to write some stuff which I'm not sure is right.I here give my code.Kindly suggest me a clear example of using zlib and also please tell me where am I wrong in the following code.


//This is a simple method "meth" where in I'm tring to compress an xlsx file
-(void)meth
{

    NSData *indata=[[NSData alloc]init];//indata is data containing the xlsx file
    [indata initWithContentsOfFile:@"./sampleSheet.xlsx"];//the xlsx file is "sampleSheet.xlsx"

    int inLength=[indata length];
    int outLength=[indata length];
    NSData *outData=[[NSData alloc] init];
    
    z_stream dstream;
    dstream.zalloc = Z_NULL;
    dstream.zfree = Z_NULL;
    dstream.opaque = Z_NULL;


    dstream.avail_in = inLength+1; 
    dstream.next_in = (Bytef *)indata; 
    dstream.avail_out = outLength; 
    dstream.next_out = (Bytef *)outData; 

    
    deflateInit(&dstream, Z_DEFAULT_COMPRESSION);
    deflate(&dstream, Z_FINISH);
    deflateEnd(&dstream);

    NSLog(@"%i",[outData length]);
    NSLog(@"%@",[outData description]);
    
 }

My outData length is always 0.Which indicates data is not compressed.Am I right?

My apologies if I asked somthing very stupid and silly.
TIA

---

### Post by r-senior on 2013-07-10
Please use code tags for code: [noparse]```
Your code here
```[/noparse]

This is a nice, reusable example of using zlib:

[http://deusty.blogspot.co.uk/2007/07/gzip-compressiondecompression.html](http://deusty.blogspot.co.uk/2007/07/gzip-compressiondecompression.html)

What he's done here is create a [category](https://developer.apple.com/library/ios/#documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/CustomizingExistingClasses/CustomizingExistingClasses.html#//apple_ref/doc/uid/TP40011210-CH6-SW1) on NSData. This means that any time you want to compress or decompress an NSData object, all you have to do is import the category header.

If you just want to compress and decompress, rather than understand zlib, I'd suggest you get your head around categories and just copy that example as a starting point (File-New-File, then choose Category in Xcode). Then you'd be able to use it like this:

```
#import "ViewController.h"
#import "NSData+Compression.h"

@implementation ViewController

- (void)viewDidLoad
{
    [super viewDidLoad];

    NSString *path = [[NSBundle mainBundle] pathForResource:@"sample" ofType:@"txt"];
    
    NSData *data = [NSData dataWithContentsOfFile:path];
    NSLog(@"Original: %d", [data length]);
    NSData *compressed = [data gzipDeflate];
    NSLog(@"Compressed: %d", [compressed length]);
    NSData *uncompressed = [compressed gzipInflate];
    NSLog(@"Uncompressed: %d", [uncompressed length]);

    NSLog(@"%@", [[NSString alloc] initWithData:uncompressed encoding:NSASCIIStringEncoding]);
    
}
@end

```

*Console output*
```
2013-07-10 08:31:18.777 Test[3818:c07] Original: 446
2013-07-10 08:31:18.779 Test[3818:c07] Compressed: 282
2013-07-10 08:31:18.779 Test[3818:c07] Uncompressed: 446
2013-07-10 08:31:18.779 Test[3818:c07] Lorem ipsum dolor sit amet, consectetur adipisicing elit ...
```

I just made a quick iPhone project to test that I could compress and decompress a file of sample text using those categories. The zlib library is in the standard list in Xcode so is easy to add.

Let me know if you get stuck.

---

### Post by priyaanand on 2013-07-11
Hi

Thanks a ton for the example.It made many things clear.I implemented my code keeping in view the example.I'm able to see that data is compressed and decompressed as well.I here post my code that I wrote.I actually want to compress an xlsx file into a zip folder and extract(decompress) the xml files(xml files of an xlsx file) in it.I have been doing that manually using Archive Mounter.How can I achieve this using zlib in objective-c?

I'm a beginner in programming and objective-C as well.So kindly excuse my ignorance.

TIA

```


//@interface

#import<Foundation/Foundation.h>
#include "zlib.h"
#define CHUNK 16384

@interface practiceClass:NSObject
{



}


-(NSMutableData *)decompressData:(NSMutableData *)dataToInflate;
-(NSMutableData *)compressData:(NSMutableData *)dataToInflate;

//@implementation

#import "practice.h"
@implementation practiceClass

-(NSMutableData *)decompressData:(NSMutableData *)dataToInflate
{
    if([dataToInflate length]==0)
    NSLog(@"Cannot decompress an empty file");
    int full_length=[dataToInflate length];
    int half_length=input_length/2;
    NSMutableData *decompData=[NSMutableData dataWithLength:(full_length+half_length)];
    
    z_stream dstream;
    dstream.next_in = (Bytef *)[dataToInflate bytes];
    dstream.avail_in = [dataToInflate length];
    dstream.total_out = 0;
    dstream.zalloc = Z_NULL;
    dstream.zfree = Z_NULL;
        
    dstream.next_out = [decompData mutableBytes] + dstream.total_out;
      dstream.avail_out = [decompData length] - dstream.total_out;
    inflate(&dstream,Z_NO_FLUSH);
    inflateEnd(&dstream);            
    return decompData;
}    

-(NSMutableData *)compressData:(NSMutableData *)dataToDeflate
{
    z_stream istream;
 
    istream.zalloc = Z_NULL;
    istream.zfree = Z_NULL;
    istream.opaque = Z_NULL;
    istream.total_out = 0;
    istream.next_in=(Bytef *)[dataToDeflate bytes];
     istream.avail_in = [dataToDeflate length];

    deflateInit(&istream,Z_DEFAULT_COMPRESSION);
    NSMutableData *compData = [NSMutableData dataWithLength:CHUNK];    
    istream.next_out = [compData mutableBytes] + istream.total_out;
     istream.avail_out = [compData length] - istream.total_out;

    
    deflate(&istream,Z_FINISH);
    deflateEnd(&istream);
     [compData setLength: istream.total_out];
    return compData;
}

@end


// main Function


#import<Foundation/Foundation.h>
#import "practice.h"
#include "zlib.h"
int main(int argc,const char *argv[])
{
    NSAutoreleasePool *pool=[[NSAutoreleasePool alloc] init];
    practiceClass *obj=[[practiceClass alloc] init];
    NSMutableData *iData=[[NSMutableData alloc] initWithContentsOfFile:@"./sampleSheet.zip"];
    NSMutableData *oData=[[NSMutableData alloc] init];

    
    oData=[obj decompressData:iData];
    NSLog(@"Input :%i",[iData length]);
    NSLog(@"Output :%i",[oData length]);

    NSLog(@"%@",[oData description]);

    
    [pool drain];
    return 0;
}

@end


```

---

