---
title: "php running checksum"
date: 2009-04-29
forum: Programming Talk
---

### Post by cdenley on 2009-04-29
I created a python application which uploads to apache by posting the file's contents in pieces along with checksums. The post is handled in apache by a php script. Currently, I compute the checksums for each piece individually, and keep a running checksum which is sent after the upload is complete.

It would be more efficient to simply send the running checksums with each piece. However, the only way I can compute the running checksum on the server-side from the php script is to compute the checksum for all uploaded data from the beginning of the file every time a piece is received. I tried storing the hashing context returned by hash_init in a session variable, then reusing the same hashing context, but this doesn't seem to work. Is this possible with PHP, to have a script continue appending data to a hash_init object from when it was previously executed, preferably by storing it in memory?

---

### Post by cdenley on 2009-04-29
I've been doing a little more research, and it appears this isn't possible, at least with session variables. Session variables store serialized data, and resource-type variables cannot be serialized with the serialize function. I'm trying to think outside the box. Is there any way to keep a hash context persistent?

---

### Post by cdenley on 2009-04-29
My only idea at the moment is to create a program in C which can compute a running MD5 checksum from stdin, saving the checksums state to a file. I would rather not resort to starting a command shell for every piece of uploaded data, if anyone has another idea.
```

#include "md5.h"
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

void print_md5(char * ret,unsigned char * sum);

int main(int argc,char *argv[])
{
    if(argc<2) {
        printf("you must give a file as an argument\n");
        return 1;
    }
    FILE *f;
    md5_state_t state;
    unsigned char digest[16];
    int exists=access(argv[1],F_OK);
    if(exists!=0) {
        md5_init(&state);
    }
    else {
        f=fopen(argv[1],"r");
        fread(&state,sizeof(state),1,f);
        fclose(f);
    }
    char buf[512] = {0};
    int size=1;
    while(size>0) {
        size=fread(buf,1,512,stdin);
        md5_append(&state,buf,size);
    }
    f=fopen(argv[1],"w");
    fwrite(&state,sizeof(state),1,f);
    fclose(f);
    md5_finish(&state, digest);
    char temp[33];
    print_md5(temp,digest);
    printf("%s\n",temp);
    return 0;
}

void print_md5(char * ret,unsigned char * sum) {
    int i;
    for(i=0;i<16;i++) {
        sprintf(&ret[i*2],"%02x",sum[i]);
    }
}

```

---

### Post by cdenley on 2009-05-01
I decided to create a php extension. It seems to work well.
```

#ifdef HAVE_CONFIG_H
#include "config.h"
#endif

#include "php.h"
#include "php_md5run.h"
#include <openssl/md5.h>

static function_entry php_md5run_functions[] = {
        PHP_FE(md5_init, NULL)
        PHP_FE(md5_append, NULL)
        PHP_FE(md5_finish, NULL)
        { NULL, NULL, NULL }
};

PHP_FUNCTION(md5_init)
{
    MD5_CTX state;
    MD5_Init(&state);
    RETURN_STRINGL(&state,sizeof(state),1);
}

PHP_FUNCTION(md5_append)
{
    char *state;
    int state_len;
    char *data;
    int data_len;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "ss", &state,&state_len,&data,&data_len) == FAILURE) {
        RETURN_NULL();
    }
    if(data_len>0)
        MD5_Update(state,data,data_len);
    RETURN_STRINGL(state,state_len,1);
}

PHP_FUNCTION(md5_finish)
{
    char *state;
    int state_len;
    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s", &state,&state_len) == FAILURE) {
        RETURN_NULL();
    }
    unsigned char digest[16];
    MD5_Final(digest,state);
    char ret[33];
    tohex(ret,digest);
    RETURN_STRING(ret,1);
}

void tohex(char * ret,unsigned char * sum) {
	int i;
	for(i=0;i<16;i++) {
		char temp[3];
		sprintf(&ret[i*2],"%02x",sum[i]);
	}
}

zend_module_entry md5run_module_entry = {
#if ZEND_MODULE_API_NO >= 20010901
        STANDARD_MODULE_HEADER,
#endif
        PHP_MD5RUN_EXTNAME,
        php_md5run_functions, /* Functions */
        NULL, /* MINIT */
        NULL, /* MSHUTDOWN */
        NULL, /* RINIT */
        NULL, /* RSHUTDOWN */
        NULL, /* MINFO */
#if ZEND_MODULE_API_NO >= 20010901
        PHP_MD5RUN_VERSION,
#endif
        STANDARD_MODULE_PROPERTIES
};

#ifdef COMPILE_DL_MD5RUN
ZEND_GET_MODULE(md5run)
#endif

```

For crc32 checksums, I found most of this code from a comment here
[http://us2.php.net/manual/en/function.crc32.php#76080](http://us2.php.net/manual/en/function.crc32.php#76080)
[PHP]
<?php
function crc32run($data,$init=false) {
    if(!$init)
        return crc32($data);
    if(!is_int($init))
        return false;
    return crc32_combine($init,crc32($data),strlen($data));
}

function crc32_combine($crc1, $crc2, $len2)
{
    $odd[0]=0xedb88320;
    $row=1;

    for($n=1;$n<32;$n++) {
        $odd[$n]=$row;
        $row<<=1;
    }

    gf2_matrix_square($even,$odd);
    gf2_matrix_square($odd,$even);

    do {
        /* apply zeros operator for this bit of len2 */
        gf2_matrix_square($even, $odd);

        if ($len2 & 1)
            $crc1=gf2_matrix_times($even, $crc1);

        $len2>>=1;
   
        /* if no more bits set, then done */
        if ($len2==0)
            break;
   
        /* another iteration of the loop with odd and even swapped */
        gf2_matrix_square($odd, $even);
        if ($len2 & 1)
            $crc1=gf2_matrix_times($odd, $crc1);
        $len2>>= 1;
   
    } while ($len2 != 0);

    $crc1 ^= $crc2;
    return $crc1;
}

function gf2_matrix_square(&$square, &$mat)
{
    for ($n=0;$n<32;$n++) {
        $square[$n]=gf2_matrix_times($mat, $mat[$n]);
    }
}

function gf2_matrix_times($mat, $vec)
{
    $sum=0;
    $i=0;
    while ($vec) {
        if ($vec & 1) {
            $sum ^= $mat[$i];
        }
        $vec>>= 1;
        $i++;
    }
    return $sum;
}
?>
[/PHP]

---

### Post by Reiger on 2009-05-01
My head is a bit tired, but I am still not following this: a checksum serves to basically verify data integrity. Now unless something can actually touch your data, it matters little whether you use a running checksum or just individual checksums for the file chunks and trust on the OS underneath to be capable of appending data to a file without borking it? That is: if you don't use a checksum like CRC32 which simply has too little 'space' to do reliable error-checking with against large files.

On the client side you are not going to notice because either way it involves (re-)computing a checksum; you can arguably increase performance by splitting in suitable chunks and doing a checksum over chunks only (because the running checksum will typically have to deal with more input data, and hence take more time to be computed).

---

### Post by cdenley on 2009-05-01
> **Reiger said:**
> My head is a bit tired, but I am still not following this: a checksum serves to basically verify data integrity. Now unless something can actually touch your data, it matters little whether you use a running checksum or just individual checksums for the file chunks and trust on the OS underneath to be capable of appending data to a file without borking it? That is: if you don't use a checksum like CRC32 which simply has too little 'space' to do reliable error-checking with against large files.

On the client side you are not going to notice because either way it involves (re-)computing a checksum; you can arguably increase performance by splitting in suitable chunks and doing a checksum over chunks only (because the running checksum will typically have to deal with more input data, and hence take more time to be computed).

Maybe I am over-thinking this, but I'll try to explain:

I'm splitting the file into pieces because:
-I want to have a progress bar, and I will increment it after each piece is sent.
-If an error is encountered, it should be able to resend the corrupt piece, not the entire file.
-Computing checksums for large files require the file to be read in pieces anyway, since 2GB won't fit into memory.

In addition to verifying the file's integrity during/after the upload, I need to store checksums for the entire file so they may be compared in the future. This requires the client application to generate checksums for the entire file in addition to checksums for pieces during the upload. Now, it verifies each piece with the checksum computed for the entire file read up to that point, requiring only one checksum for each algorithm. An error is not only detected, but corrected during the upload process. I even used threading so the checksums are computed for the next piece while the previous is still being sent.

I guess I could generate whole-file checksums on the server-side after the upload is complete, now that I think about it. If the checksums for each piece match, then the entire file's checksums would match as well. The only problem with that would be if it wasn't written to disk on the server correctly. It also just seems safer to compute the checksum from the original file on the uploader's system. After all, verifying an upload with MD5 and CRC32 is only to satisfy the paranoid.

---

### Post by Reiger on 2009-05-01
> **cdenley said:**
> Maybe I am over-thinking this, but I'll try to explain:

I'm splitting the file into pieces because:
-I want to have a progress bar, and I will increment it after each piece is sent.
-If an error is encountered, it should be able to resend the corrupt piece, not the entire file.
-Computing checksums for large files require the file to be read in pieces anyway, since 2GB won't fit into memory.

In addition to verifying the file's integrity during/after the upload, I need to store checksums for the entire file **so they may be compared in the future**. 

Yeah that (the bolded bit) was not immediately obvious to me from the start. It makes a lot more sense to me now. :)

I am not sure (I only use it for lock variables, to control on disk caches with etc.), but maybe you can use it [the APC PECL extentsion] for non primitive values as well: [http://nl2.php.net/manual/en/function.apc-add.php](http://nl2.php.net/manual/en/function.apc-add.php).

---

