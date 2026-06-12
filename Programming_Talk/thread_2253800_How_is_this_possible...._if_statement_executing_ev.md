---
title: "How is this possible.... if statement executing even though condition is not true."
date: 2014-11-22
forum: Programming Talk
---

### Post by SagaciousKJB on 2014-11-22
Okay so I had to open up my debugger to check this out after the program wasn't operating correctly.  Rather than only show my whole source, here is the debugger window...

[[IMG]http://i1266.photobucket.com/albums/jj528/sagaciouskjb/Screenshot-11222014-100002AM.png[/IMG]](http://s1266.photobucket.com/user/sagaciouskjb/media/Screenshot-11222014-100002AM.png.html)

So gdb is showing that at line 197, options.entryGiven equals 1.

Then, the if statement tests if options.entryGiven is some random number I jotted in...

And yet it executes!  Event hough gdb clearly shows options.entryGiven still equals 1.


What in the world is going on?

Here is my source, with the if statement shown commented out so it will work for now...

```
#include <unistd.h>
#include <stdio.h>                                           
#include <stdlib.h>                                          
#include <string.h>                                          
#include <time.h>                                            
#include <errno.h>   
#include <sys/types.h>
#include <sys/stat.h>  
#include "xcet.h"
#include "getpass.h"
#include "aes.c"

/*Define a size for the buffers.  Was originally BUFFER_SIZES, but this proved to be insufficient space*/
#define BUFFER_SIZES 512

/*Structure to hold options, toggle on with 1*/
struct optionsStruct         
{                            
  int Add; /*To add a password to a file*/             
  int Read; /*To read a password to a file*/
  int Delete; /*To delete an entry from a file*/
  int passArg; /*To enable passing the password from the command line*/
  int xcetpassArg; /*To enable passing the xcet password from the command line*/
  int fileGiven; /*To ensure that a file has been specified, program halts if not set to 1*/
  int entryGiven;
  char passWordFileName[256]; /*Password file name*/
  int entrySearch; /*Use to find a specific entry instead of operating on all of them*/
}; /*I should probably initialize all to zero to be extra careful, but I'm not gonna*/

struct optionsStruct options; /*Pretty bland name for our structure, but it works*/

int main(int argc, char *argv[])
{                               

  /*Gotta give some kind of option...*/
  if(argc == 1)
    {            
      printSyntax(argv[0]);
      return 1;            
    }      
  options.entryGiven = 0;

  FILE *passWordFile = NULL;
  /*Make array for passWord and entryName BUFFER_SIZES characters long
    Since the usernames and passwords aren't likely to be longer than this
    we might as well just specify an arbitrary size of sufficient space*/
  char *passWord = malloc(sizeof(char) * BUFFER_SIZES);                                          
  char entryName[BUFFER_SIZES];                                         
  /*Allow long xcet passes since they shouldn't be limited in any way*/                                  
  char *xcetPass = malloc(sizeof(char) * BUFFER_SIZES);                                         
  int i, opt, seed = 0; /*You need an iterator, a seed for random functions and a variable for getop()*/                                  
  int errflg = 0; /*Toggle this flag on and off so we can check for errors and act accordingly*/

  const EVP_CIPHER *cipher;
  const EVP_MD *dgst = NULL;
  unsigned char key[EVP_MAX_KEY_LENGTH], iv[EVP_MAX_IV_LENGTH], hash[20], *tmpBuffer;
  const unsigned char *salt = NULL;
  FILE *in, *out;


  OpenSSL_add_all_algorithms();

  /*Fill up passWord and entryName arrays with random bytes so the padding space isn't predictable.*/
  for(i = 0; i < BUFFER_SIZES; i++)                                    
    passWord[i] = random() % 256;                        
  for(i = 0; i < BUFFER_SIZES; i++)                                    
    entryName[i] = random() % 256;                       

  /*Process through arguments
    if someone other than the author spots a problem go ahead and fix it*/
  while ((opt = getopt(argc, argv, "n:p:x:f:hard")) != -1)
    {
      switch(opt)
	{
	case 'h': /*Help*/
	  printSyntax("passmanager");
	  return 1;
	  break;
	case 'a': /*Add passwords*/
	  options.Add = 1;
	  break;
	case 'r': /*Read passwords*/
	  options.Read = 1;
	  break;
	case 'd': /*Delete passwords*/
	  options.Delete = 1;
	  break;
	case 'f': /*Specify password file*/
	  if(options.Add == 1)
	    {
	      passWordFile = fopen(optarg, "ab");
	      if(passWordFile == NULL) /*Make sure the file opens*/
		{                                                      
		  perror(argv[0]);
		  printf("\n Filename : %s\n",optarg);
		  return errno;                                  
		}
	      strcpy(options.passWordFileName, optarg);
	    }
	  if(options.Read == 1)
	    {
	      passWordFile = fopen(optarg, "rb");
	      if(passWordFile == NULL) /*Make sure the file opens*/
		{        
		  perror(argv[0]);
		  printf("\n Filename: %s\n",optarg);
		  return errno;                                  
		}
		
	      strcpy(options.passWordFileName, optarg);
	    }
	  if(options.Delete == 1)
	    {
	      passWordFile = fopen(optarg, "rb+");
	      if(passWordFile == NULL) /*Make sure the file opens*/
		{                                                      
		  perror(argv[0]);
		  printf("\n Filename: %s\n",optarg);
		  return errno;                                  
		}
	      strcpy(options.passWordFileName, optarg);
	    }
	  options.fileGiven = 1;
	  break;
	case 'n': /*Specifies an entry by name*/
	  if(optarg[0] == '-')
	    {
	      printf("Option -n requires an operand\n");
	      errflg++; /*Set the error flag so program will halt after getopt() is done*/
	    }
	  else
	    options.entrySearch = 1;
	  if(strlen(optarg) > BUFFER_SIZES)
	    {
	      printf("entry name too long");
	      printSyntax("passmanager");
	      return 1;
	    }
	  strcpy(entryName, optarg);
	  options.entryGiven = 1;
	  break;
	case 'p': /*If passing password from command line*/
	  options.passArg = 1;
	  if(optarg[0] == '-' && strlen(optarg) == 2)
	    {       
	      printf("Option -p requires an operand\n");
	      errflg++; /*Set error flag*/
	    }
	  if(strlen(optarg) > BUFFER_SIZES)
	    {
	      printf("password too long");
	      errflg++; /*Set error flat*/
	    }
	  strcpy(passWord, optarg);
	  break;
	case 'x': /*If passing xcet password from command line*/
	  options.xcetpassArg = 1;
	  if(optarg[0] == '-' && strlen(optarg) == 2)
	    {
	      errflg++; /*Set error flag*/
	      printf("Option -x requires an operand\n");
	    }
	  strcpy(xcetPass, optarg);			break;
	  break;
	case ':':
	  printf("Option -%c requires an operand\n", optopt);
	  errflg++; /*Set error flag*/
	  break;
	case '?': /*Get opt error handling*/
	  if (optopt == 'n')
	    fprintf (stderr, "Option -%c requires an argument.\n", optopt);
	  if (optopt == 'f')
	    fprintf (stderr, "Option -%c requires an argument.\n", optopt);
	  if (optopt == 'x')
	    fprintf (stderr, "Option -%c requires an argument.\n", optopt);
	  if (optopt == 'p')
	    fprintf (stderr, "Option -%c requires an argument.\n", optopt);
	  printf("Unrecognized option: -%c\n", optopt);
	  errflg++; /*Set error flag*/
	}
    }
  /*If the user didn't specify a file with -f set error flag on*/
  if(options.fileGiven != 1)
    errflg++;
  /*Finally test for errflag and halt program if on*/
  if(errflg)
    {
      printSyntax("passmanger"); /*Print proper usage of program*/
      return 1;
    }
	
  if(options.Add == 1) /*Test if we're adding a password*/
    {                   

      /* if(options.entryGiven == 878387373); */
      /* { */
      /* 	printf("\nNo entry name was specified\n"); */
      /* 	return 1; */
      /* } */

      if(passWordFile == NULL) /*Make sure the file opened*/
	{                       
	  perror(argv[0]);
	  return errno;   
	}
      if(options.passArg != 1) /*Do this unless user specified password on command line, not a good idea but I left it in for functionality*/
	{
	  passWord = getpass("Enter password to be saved: "); /*getpass() defined in getportacblech.h to retrieve pass without echo*/
	  if(strcmp(passWord,getpass("Verify password:")) != 0)
	    {
	      printf("\nPasswords do not match.  Nothing done.\n\n");
	      return 1;
	    }
	  printf("\n");
	}
      if(options.xcetpassArg != 1) /*If user did not specify to take pass off command line*/
	{
	  xcetPass = getpass("Enter xcet password to encode with: "); /*getpass() defined in getportablech.h to retrieve pass without echo*/
	  if(doesFileExist(options.passWordFileName) == 0)
	    {
	      if(strcmp(xcetPass,getpass("Verify password: ")) != 0)
		{
		  printf("\nPasswords do not match.  Nothing done.\n\n");
		  return 1;
		}
	    }
	  printf("\n");
	}
      /*Do openssl decryption so we can read encapsulated xcet encrypted data*/
      
      if(doesFileExist(options.passWordFileName) > 0) /*doesFileExists returns filesize, so if zero the file isn't encrypted, thus no decryption is necessary*/
	{
	  /*These functions generate proper iv and key for chosen openssl cipher*/
	  cipher = EVP_get_cipherbyname("aes-256-cbc");
	  if(!cipher) { fprintf(stderr, "no such cipher\n"); return 1; }

	  dgst=EVP_get_digestbyname("md5");
	  if(!dgst) { fprintf(stderr, "no such digest\n"); return 1; }

	  if(!EVP_BytesToKey(cipher, dgst, salt,
			     (unsigned char *) xcetPass,
			     strlen(xcetPass), 1, key, iv))
	    {
	      fprintf(stderr, "EVP_BytesToKey failed\n");
	      return 1;
	    }
	  fclose(passWordFile);
	  in = fopen(options.passWordFileName,"rb");
	  if(in == NULL) /*Make sure the file opens*/
	    {                                                      
	      perror(argv[0]);                               
	      return errno;                                  
	    }
	  out = fopen("passman.tmp","wb");
	  if(out == NULL) /*Make sure the file opens*/
	    {                                                      
	      perror(argv[0]);                               
	      return errno;                                  
	    }
	  decrypt(in,out,key,iv);
	  fclose(in);
	  fclose(out);

	  /*Read hash in, then strip it and write data back out to temp file*/
	  in = fopen("passman.tmp","rb");
	  if(in == NULL) /*Make sure the file opens*/
	    {                                                      
	      perror(argv[0]);                               
	      return errno;                                  
	    }
	  out = fopen("passman_2.tmp","wb"); 
	  if(out == NULL) /*Make sure the file opens*/
	    {                                                      
	      perror(argv[0]);                               
	      return errno;                                  
	    }
	  long fileSize;      
	  fseek(in, 0L, SEEK_END);
	  fileSize = ftell(in);   
	  fseek(in, fileSize - 16, SEEK_SET);

	  fread(hash,sizeof(unsigned char),16,in);

	  fseek(in, 0L, SEEK_SET);

	  tmpBuffer = malloc(sizeof(unsigned char) * (fileSize - 16));

	  fread(tmpBuffer,sizeof(unsigned char),fileSize - 16,in);
	  fwrite(tmpBuffer,sizeof(unsigned char),fileSize - 16,out);
       
	  fclose(in);
	  fclose(out);

	  wipeFile("passman.tmp");
	  remove("passman.tmp");

	  if(strncmp(hash,iv,16) != 0)
	    {
	      printf("This password seems incorrect.  Quitting to prevent data loss\n");
	      wipeFile("passman_2.tmp");
	      remove("passman_2.tmp");
	      return 1;
	    }
	  
	}

      /*Open a temporary file to write xcet data to*/
      passWordFile = fopen("passman_2.tmp","ab");
      if(passWordFile == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      writePass(passWordFile, passWord, entryName, xcetPass); /*Write xcet encrypted data to temporary file*/

      /*These functions provide proper key and iv for aes cipher, or whatever is provided by name to EVP_get_cipherbybame*/
      cipher = EVP_get_cipherbyname("aes-256-cbc");
      if(!cipher) { fprintf(stderr, "no such cipher\n"); return 1; }

      dgst=EVP_get_digestbyname("md5");
      if(!dgst) { fprintf(stderr, "no such digest\n"); return 1; }

      if(!EVP_BytesToKey(cipher, dgst, salt,
			 (unsigned char *) xcetPass,
			 strlen(xcetPass), 1, key, iv))
	{
	  fprintf(stderr, "EVP_BytesToKey failed\n");
	  return 1;
	}

      /*Now we're going to apend IV to file to act as a hash*/
      passWordFile = fopen("passman_2.tmp","ab");
      if(passWordFile == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}

      fwrite(iv,sizeof(unsigned char),16,passWordFile);
      fclose(passWordFile);

      in = fopen("passman_2.tmp","rb");
      if(in == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      out = fopen(options.passWordFileName,"wb");
      if(out == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      /*Encapsulate xcet encryption from tempfile into openssel encryption*/
         
      /*Refer to aes.c for this function*/
      encrypt(in,out,key,iv);
      fclose(in);
      fclose(out);

      /*Now overwrite the data in passman.tmp so we don't leave sensitive data behind on disk*/
      wipeFile("passman_2.tmp");
      remove("passman_2.tmp");


    }
  else if(options.Read == 1) /*Reading passes instead of adding them*/
    {
      fclose(passWordFile);
      FILE *in = fopen(options.passWordFileName,"rb");
      if(in == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      FILE *out = fopen("passman.tmp","wb"); /*Store the encapsulated xcet data in this file after openssl decryption*/
      if(out == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      /*Do openssl decryption on encapsulated xcet encrypted data*/
      if(options.xcetpassArg != 1) /*If user did not specify to take pass off command line*/
	{
	  xcetPass = getpass("Enter xcet password to decode with: "); /*getpass() defined in getportablech.h to retrieve pass without echo*/
	  printf("\n");                         
	}
      
      /*Generate proper key and iv*/
      cipher = EVP_get_cipherbyname("aes-256-cbc");
      if(!cipher) { fprintf(stderr, "no such cipher\n"); return 1; }

      dgst=EVP_get_digestbyname("md5");
      if(!dgst) { fprintf(stderr, "no such digest\n"); return 1; }

      if(!EVP_BytesToKey(cipher, dgst, salt,
			 (unsigned char *) xcetPass,
			 strlen(xcetPass), 1, key, iv))
	{
	  fprintf(stderr, "EVP_BytesToKey failed\n");
	  return 1;
	}

      /*in aes.c*/
      decrypt(in,out,key,iv);

      fclose(in);
      fclose(out);

      /*Read hash in, then strip it and write data back out to temp file*/
      in = fopen("passman.tmp","rb");
      if(in == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      out = fopen("passman_2.tmp","wb"); 
      if(out == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      long fileSize;      
      fseek(in, 0L, SEEK_END);
      fileSize = ftell(in);   
      fseek(in, fileSize - 16, SEEK_SET);

      fread(hash,sizeof(unsigned char),16,in);

      fseek(in, 0L, SEEK_SET);

	tmpBuffer = malloc(sizeof(unsigned char) * (fileSize - 16));

      fread(tmpBuffer,sizeof(unsigned char),fileSize - 16,in);
      fwrite(tmpBuffer,sizeof(unsigned char),fileSize - 16,out);
       
      fclose(in);
      fclose(out);

      wipeFile("passman.tmp");
      remove("passman.tmp");

      if(strncmp(hash,iv,16) != 0)
	{
	  printf("This password seems incorrect.  Quitting to prevent data loss\n");
	  wipeFile("passman_2.tmp");
	  remove("passman_2.tmp");
	  return 1;
	}

      passWordFile = fopen("passman_2.tmp","rb"); /*Now open the temporary file to be read as XCET data*/
      if(passWordFile == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      if(options.entrySearch == 1) /*Find a specific entry to modify*/
	printPasses(passWordFile, xcetPass, entryName); /*Function to read and decrypt passes*/
      else                                                   
	printPasses(passWordFile, xcetPass, NULL); /*Function to read and decrypt passes*/

      fclose(passWordFile);
      
      /*Now overwrite data in passman.tmp so no sensitive data is left on disk*/
      wipeFile("passman_2.tmp");
      remove("passman_2.tmp");
    }                 
  else if(options.Delete == 1) /*Delete a specified entry*/
    {    

      /* if(options.entryGiven != 1); */
      /* { */
      /* 	printf("\nNo entry name was specified\n"); */
      /* 	return 1; */
      /* } */
 
      fclose(passWordFile);
      in = fopen(options.passWordFileName,"rb");
      if(in == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      out = fopen("passman.tmp","wb"); /*Temporary file to store encapsulated xcet data*/
      if(out == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      /*Do blowfish decryption on xcet encrypted data*/

      if(options.xcetpassArg != 1) /*If user did not specify to take pass off command line*/
	{
	  xcetPass = getpass("Enter xcet password: "); /*getpass() defined in getportablech.h to retrieve pass without echo*/
	  printf("\n");                                                      
	}

      /*Generate proper key and iv*/
      cipher = EVP_get_cipherbyname("aes-256-cbc");
      if(!cipher) { fprintf(stderr, "no such cipher\n"); return 1; }

      dgst=EVP_get_digestbyname("md5");
      if(!dgst) { fprintf(stderr, "no such digest\n"); return 1; }

      if(!EVP_BytesToKey(cipher, dgst, salt,
			 (unsigned char *) xcetPass,
			 strlen(xcetPass), 1, key, iv))
	{
	  fprintf(stderr, "EVP_BytesToKey failed\n");
	  return 1;
	}

      /*in aes.c*/
      decrypt(in,out,key,iv);
      fclose(in);
      fclose(out);

      /*Read hash in, then strip it and write data back out to temp file*/
      in = fopen("passman.tmp","rb");
      if(in == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      out = fopen("passman_2.tmp","wb"); 
      if(out == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      long fileSize;      
      fseek(in, 0L, SEEK_END);
      fileSize = ftell(in);   
      fseek(in, fileSize - 16, SEEK_SET);

      fread(hash,sizeof(unsigned char),16,in);

      fseek(in, 0L, SEEK_SET);

      tmpBuffer = malloc(sizeof(unsigned char) * (fileSize - 16));

      fread(tmpBuffer,sizeof(unsigned char),fileSize - 16,in);
      fwrite(tmpBuffer,sizeof(unsigned char),fileSize - 16,out);
       
      fclose(in);
      fclose(out);

      wipeFile("passman.tmp");
      remove("passman.tmp");

      if(strncmp(hash,iv,16) != 0)
	{
	  printf("This password seems incorrect.  Quitting to prevent data loss\n");
	  wipeFile("passman_2.tmp");
	  remove("passman_2.tmp");
	  return 1;
	}

      passWordFile = fopen("passman_2.tmp","rb+"); /*Open a temporary file*/                                                         
      if(passWordFile == NULL) /*Make sure file opened*/  
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}

      if(options.entrySearch == 1) /*Only write the entry to the temporary file if it is not the entry specified*/
	deletePass(passWordFile, xcetPass, entryName); /*Function to delete entry from file*/
      else                                                   
	{                                                      
	  printSyntax("passmanager"); /*Don't delete anything if an entry wasn't specified*/                    
	  return 1;                                      
	}

      cipher = EVP_get_cipherbyname("aes-256-cbc");
      if(!cipher) { fprintf(stderr, "no such cipher\n"); return 1; }

      dgst=EVP_get_digestbyname("md5");
      if(!dgst) { fprintf(stderr, "no such digest\n"); return 1; }

      if(!EVP_BytesToKey(cipher, dgst, salt,
			 (unsigned char *) xcetPass,
			 strlen(xcetPass), 1, key, iv))
	{
	  fprintf(stderr, "EVP_BytesToKey failed\n");
	  return 1;
	}

      /*Now we're going to apend IV to file to act as a hash*/
      passWordFile = fopen("passman__delete.tmp","ab");
      if(passWordFile == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}

      fwrite(iv,sizeof(unsigned char),16,passWordFile);
      fclose(passWordFile);

      in = fopen("passman__delete.tmp","rb"); /*Now we open a second temporary file deletePass made for us to read in the xcet data*/
      if(in == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}
      out = fopen(options.passWordFileName,"wb");
      if(out == NULL) /*Make sure the file opens*/
	{                                                      
	  perror(argv[0]);                               
	  return errno;                                  
	}

      /*Encapsulate xcet data in openssl encryption*/
      
      encrypt(in,out,key,iv);
      fclose(in);
      fclose(out);

      /*Wiping sensitive data off disk*/
      wipeFile("passman_2.tmp");
      wipeFile("passman__delete.tmp");
      remove("passman_2.tmp");
      remove("passman__delete.tmp");


    }                                                              
  else                                                           
    {                                                              
      printSyntax("passmanager"); /*Just in case something else happens...*/                            
      return 1;                                              
    }                                                              

  free(xcetPass);
  free(passWord);
  return 0;
}                

/*Print the passwords using the filename, xcetPass and if needed the entryname as arguments*/
int printPasses(FILE *passWordFile, char *xcetPass, char *searchString)
{                                                                      
  char entryName[BUFFER_SIZES];                                            
  char passWord[BUFFER_SIZES];                                             
  long int passLength;                                           
  int i, ii = 0;                                                 

  /*Declare variables for xcet operations and initialize them while we are at it*/
  int pblen = 1, bfvar_onetimepad = 0, keylen = strlen(xcetPass);

  /*xcetBuffer stores both entryName and passWord in an encrypted form*/
  char *xcetBuffer = malloc(sizeof(char) * BUFFER_SIZES * 2);                         
  char *entryBuffer = malloc(sizeof(char) * BUFFER_SIZES);                        
  char *passBuffer = malloc(sizeof(char) * BUFFER_SIZES);                         

  /*Get the filesize*/
  long fileSize;      
  fseek(passWordFile, 0L, SEEK_END);
  fileSize = ftell(passWordFile);   
  fseek(passWordFile, 0L, SEEK_SET);

  while(1)
    {       
      /*I've had better luck using this than with feof to tell when I've reached the end of file*/
      if(ftell(passWordFile) >= fileSize)               
	break;                                    

      /*Initialize xcet variables according to xcet.h, and one for incrementing, we need to do this each time we plan to encrypt/decrypt data*/
      ii = 0;                                                
      pblen = 1, bfvar_onetimepad = 0;                       

      /*Read the entryname and then the password into entryBuffer and passBuffer respectively*/
      fread(entryBuffer,BUFFER_SIZES,sizeof(char), passWordFile);                                        
      fread(passBuffer,BUFFER_SIZES,sizeof(char), passWordFile);                                         

      /*Copy the encrypted information into the xcetBuffer*/
      for(i = 0; i < BUFFER_SIZES; i++)                               
	xcetBuffer[i] = entryBuffer[i];               
      for(i = 0; i < BUFFER_SIZES; i++)                               
	xcetBuffer[i + BUFFER_SIZES] = passBuffer[i];           
      /*Decrypt the xcetbuffer, and place decrypted bytes into entryBuffer and passBuffer where appropriate*/
      for(i = 0; i < BUFFER_SIZES * 2; i++)                                                                                 
	{                                                                                                       
	  /*Generate appropriate bfvar_onetimepad value*/                                                                                   
	  bfvar_onetimepad = bfvar_gen(bfvar_onetimepad, xcetPass[ii]);                                   
	  if(i < BUFFER_SIZES) /*Use first BUFFER_SIZES bytes as entryName*/                                  
	    entryBuffer[i] = xcet(xcetBuffer[i],xcetPass[ii],keylen,pblen,bfvar_onetimepad); /*this is the xcet decryption*/
	  else /*Once BUFFER_SIZES bytes read, split the next BUFFER_SIZES into passBuffer*/                                                                                             
	    passBuffer[i - BUFFER_SIZES] = xcet(xcetBuffer[i],xcetPass[ii],keylen,pblen,bfvar_onetimepad);                            

	  /*Generate pblen after bfvar_onetimepad generation and xcet operation*/
	  pblen = pblen_gen(pblen, bfvar_onetimepad);

	  /*Keep iteration from going out of bounds on xcetPass*/
	  if(ii > keylen)                                       
	    ii = 0;                                        
	  else if(ii < keylen)
	    ii++;
	}                                                              

      if(searchString != NULL) /*If an entry name was specified*/
	{                       
	  if(strcmp(searchString, entryBuffer) == 0) /*Find specified string and print only that*/
	    printf("%s : %s\n", entryBuffer, passBuffer);
	}                                                            
      else /*If an entry name wasn't specified, print them all*/
	printf("%s : %s\n", entryBuffer, passBuffer);        

    }
  return 0;
}                

/*Finds and removes a specific entry from the file*/
int deletePass(FILE *passWordFile, char *xcetPass, char *searchString)
{                                                                      
  char entryName[BUFFER_SIZES];                                            
  char passWord[BUFFER_SIZES];                                             
  long int passLength;                                           
  int i, ii = 0, iii = 0; /*We need iterators!*/             

  char *fileBuffer; /*We're gonna store the data in a buffer to modify it*/                    

  FILE *tmpFile;

  /*Declare variables for xcet operations*/
  int pblen = 1, bfvar_onetimepad = 0, keylen = strlen(xcetPass);

  /*xcetBuffer stores both entryName and passWord in an encrypted form*/
  char *xcetBuffer = malloc(sizeof(char) * BUFFER_SIZES * 2);                         
  char *entryBuffer = malloc(sizeof(char) * BUFFER_SIZES);                        
  char *passBuffer = malloc(sizeof(char) * BUFFER_SIZES);                         

  /*Get the filesize*/
  long fileSize;      
  fseek(passWordFile, 0L, SEEK_END);
  fileSize = ftell(passWordFile);   
  fseek(passWordFile, 0L, SEEK_SET);

  /*Now make a buffer for the file, minus the size of the entry*/
  fileBuffer = malloc((sizeof(char) * fileSize) - BUFFER_SIZES * 2);           

  while(1)
    {       
      /*I've had better luck using this than with feof*/
      if(ftell(passWordFile) >= fileSize)               
	break;                                    

      /*Initialize xcet variables, and one for iterators. Remember this needs to be done for every encryption/decryption*/
      ii = 0;                                                
      pblen = 1, bfvar_onetimepad = 0;                       

      /*Read the entryname and then the password into entryBuffer and passBuffer respectively*/
      fread(entryBuffer,BUFFER_SIZES,sizeof(char), passWordFile);                                        
      fread(passBuffer,BUFFER_SIZES,sizeof(char), passWordFile);                                         

      /*Copy the encrypted information into the xcetBuffer, processing the whole BUFFER_SIZES * 2 bytes in halves*/
      for(i = 0; i < BUFFER_SIZES; i++)                               
	xcetBuffer[i] = entryBuffer[i];               
      for(i = 0; i < BUFFER_SIZES; i++)                               
	xcetBuffer[i + BUFFER_SIZES] = passBuffer[i];           
      /*Decrypt the xcetbuffer, and place decrypted bytes into entryBuffer and passBuffer*/
      for(i = 0; i < BUFFER_SIZES * 2; i++)                                                                                 
	{                                                                                                       
	  /*Generating the bfvar_onetimepad*/                                                                                   
	  bfvar_onetimepad = bfvar_gen(bfvar_onetimepad, xcetPass[ii]);                                   
	  if(i < BUFFER_SIZES) /*Store the first BUFFER_SIZES bytes into the entryBuffer*/                                                                                      
	    entryBuffer[i] = xcet(xcetBuffer[i],xcetPass[ii],keylen,pblen,bfvar_onetimepad); /*Run the xcet function with the appropriately primed variables*/
	  else /*Store the next BUFFER_SIZES bytes into the passBuffer*/                                                            
	    passBuffer[i - BUFFER_SIZES] = xcet(xcetBuffer[i],xcetPass[ii],keylen,pblen,bfvar_onetimepad); /*Continue the xcet decryption on the rest of data*/

	  /*Generate the pblen in preparation for next round*/
	  pblen = pblen_gen(pblen, bfvar_onetimepad);

	  /*Increment through entryBuffer and passBuffer using keylen to check bounds*/
	  if(ii > keylen)                                       
	    ii = 0;                                        
	  else if( ii < keylen)
	    ii++;
	}                                                              

      /*Initialize xcet variables for next encryption/decryption*/
      ii = 0;                                                
      pblen = 1, bfvar_onetimepad = 0;                       

      if(strcmp(searchString, entryBuffer) != 0) /*Now we're going to find the specific entry to delete it*/
	{                                         
	  for(i = 0; i < BUFFER_SIZES * 2; i++)           
	    {                                 
	      /*xcet junk*/             
	      bfvar_onetimepad = bfvar_gen(bfvar_onetimepad, xcetPass[ii]);

	      /*Fill the fileBuffer with the BUFFER_SIZES * 2 bytes that compose both entryBuffer and passBuffer*/
	      if(i < BUFFER_SIZES)                                                   
		fileBuffer[iii] = xcet(entryBuffer[i],xcetPass[ii],keylen,pblen,bfvar_onetimepad);
	      else                                                                                      
		fileBuffer[iii] = xcet(passBuffer[i - BUFFER_SIZES],xcetPass[ii],keylen,pblen,bfvar_onetimepad);

	      /*xcet junk*/
	      pblen = pblen_gen(pblen, bfvar_onetimepad);
	      
	      /*Increment fileBuffer position*/
	      iii++;
		
	      /*Increment through entryBuffer and passBuffer and use keylen to check bounds*/
	      if(ii > keylen)
		ii = 0;
	      else if(ii < keylen)
		ii++;
	    }             
	}                     

    }

  /*Close password file
    write fileBuffer to the temp file and close
    remove the old password file and overwrite with the new one
    I should probably find a way to do this that cannot accidentally result
    in the loss of data if the program or computer crashed unexpectedly*/
  fclose(passWordFile);

  tmpFile = fopen("passman__delete.tmp","wb");/*Now open a temp file just to write the new xcet data to, clean up in the calling function*/
  if(tmpFile == NULL) /*Make sure the file opens*/
    {                                                      
      perror("passmanager");                               
      return errno;                                  
    }
  fwrite(fileBuffer, fileSize - BUFFER_SIZES * 2, sizeof(char), tmpFile);
  fclose(tmpFile);                                         

  return 0;                                       
}                                                       

int writePass(FILE *passWordFile, char *passWord, char *entryName, char *xcetPass)
{
  /*We need a set of incrementors to crawl through buffers*/
  int i, ii = 0;                                                            

  /*Priming the variables needed of xcet encryption*/
  int pblen = 1, bfvar_onetimepad = 0, keylen = strlen(xcetPass);

  /*passWord and entryName are both copied into infoBuffer, which is then encrypted with xcet into xcetBuffer and written*/
  char *infoBuffer = malloc(sizeof(char) * BUFFER_SIZES * 2);                                                                             
  char *xcetBuffer = malloc(sizeof(char) * BUFFER_SIZES * 2);                                                                             

  /*Put the bytes, include random whitespace ones, from entryName and passWord into infoBuffer, again splitting the BUFFER_SIZES * 2 bytes between the two*/
  for(i = 0; i < BUFFER_SIZES; i++)                                                            
    infoBuffer[i] = entryName[i];                                              
  for(i = 0; i < BUFFER_SIZES; i++)
    infoBuffer[i + BUFFER_SIZES] = passWord[i];
  /*This looping operation is different than the one in printPasses, because it encrypts and writes the whole buffer to file*/
  for(i = 0; i < BUFFER_SIZES * 2; i++)
    {
      /*Better documentation for the xcet operations to come*/
      bfvar_onetimepad = bfvar_gen(bfvar_onetimepad, xcetPass[ii]);
      xcetBuffer[i] = xcet(infoBuffer[i],xcetPass[ii],keylen,pblen,bfvar_onetimepad);
      pblen = pblen_gen(pblen, bfvar_onetimepad);

      /*Increment through xcetPass buffer and use keylen to check bounds*/
      if(ii > keylen)
	ii = 0;
      else if(ii < keylen)
	ii++;
    }

  /*Write the encrypted information to file*/
  fwrite(xcetBuffer,1,sizeof(char) * BUFFER_SIZES * 2,passWordFile);

  fclose(passWordFile);
  return 0;
}

int wipeFile(const char *filename)
{
  int fileSize = doesFileExist(filename);
  int i,ii;
  FILE *fileToWrite;
  for(ii=0; ii <=25; ii++)
    {
      fileToWrite = fopen(filename,"wb");
      if(fileToWrite == NULL) /*Make sure the file opens*/
	{                                                      
	  perror("passmanager");                               
	  return errno;                                  
	}
      for(i=0; i <= fileSize; i++)
	{
	  fprintf(fileToWrite,"%c",'\0');
	}
      fclose(fileToWrite);
    }
  return 0;
}

  
/*Kind of a confusing name, but will return the filesize.  If it's zero you can be reasonably sure the file doesn't exist.  Not to be confused with whether the system could open or not*/
int doesFileExist(const char *filename) {
  struct stat st;
  int result = stat(filename, &st);
  return st.st_size;
}

int printSyntax(char *arg)
{
  printf("%s [-a | -r | -d] [-n -p] -x xcetPass -f passFile\n-a add mode (if selected password is not the same for those already in file, exit on failure)\n\t-n entry name up to 1024 characters\n\t-p password up to 1024 characters (don't call to be prompted for pass instead)\n-r read mode\n\t-n specifies which entry to read\t\n-d delete mode(ALWAYS MAKE A BACKUP FIRST)\n\t-n specifies entry to delete\n-n entry specifcation requires all entries be saved under the same xcetPass\n-x xcetPass (required for -r,-a,or -d) (don't call to be prompted instead)\n-f password file ( must be specified after -r,-a, and -d )\n-h this help page\n", arg);
  return 1;
}

```

---

### Post by trent.josephsen on 2014-11-22
I read the title, and I said to myself... "Semicolon."

Lo and behold, a stray semicolon after the if(...)!

Not to start a style war, but this is one reason I prefer the One True Brace Style -- it's less prone to semicolon accidents than styles that separate the opening { from its control statement.

---

### Post by SagaciousKJB on 2014-11-22
> **trent.josephsen said:**
> I read the title, and I said to myself... "Semicolon."

Lo and behold, a stray semicolon after the if(...)!

Not to start a style war, but this is one reason I prefer the One True Brace Style -- it's less prone to semicolon accidents than styles that separate the opening { from its control statement.

Oh man thank you!  I wouldn't have noticed that for the longest time.

Is the style you speak of when like this?

```

somefunction(){
    functionstuff
}

```

---

### Post by trent.josephsen on 2014-11-22
Yes, except it doesn't actually apply to your example, because K&R/OTBS styles don't put the { of a function body on the same line as its declaration. (This is for some reason called "cuddling".) Note that if I accidentally added a semicolon in the same place:
```
int somefunction(void); // <-- here
{
    /* function body */
}
```

the file would then fail to compile (good), not silently do the wrong thing (bad) as the original example did. So the argument for cuddling the { isn't as strong for function definitions as it is for loops and if-statements.

Style points are always very subjective. My ideal is basically the [Linux kernel style guidelines](https://www.kernel.org/doc/Documentation/CodingStyle), except I always use braces per [OTBS](http://en.wikipedia.org/wiki/Indent_style#Variant:_1TBS), and I resize my tabs to be 4 spaces instead of 8. But you don't have to do what I think is right, especially since we have nice tools like GNU indent to reformat code for us. I suggest you pick a style you like and use it consistently. (But if you pick some other style, and continue to have semicolon trouble, don't say I didn't warn you :-))

---

### Post by spjackson on 2014-11-22
> **SagaciousKJB said:**
> I wouldn't have noticed that for the longest time.

I can't imagine there are many C programmers who have never been bitten by this, if not in their own code then in somebody else's.

As it happens, -Wextra helps you.
```

$ cat iffy.c 
#include <stdio.h>

int main(int argc, char * argv[])
{
    if (argc > 1);
    {
        printf("Got an arg\n");
    }
    return 0;
}
$ gcc -Wall -Wextra iffy.c   -o iffy 
iffy.c: In function &#8216;main&#8217;:
iffy.c:7:18: warning: suggest braces around empty body in an &#8216;if&#8217; statement [-Wempty-body]
     if (argc > 1);
                  ^
iffy.c:4:27: warning: unused parameter &#8216;argv&#8217; [-Wunused-parameter]
 int main(int argc, char * argv[])
                         ^

```

---

### Post by dwhitney67 on 2014-11-22
> **trent.josephsen said:**
> Y I suggest you pick a style you like and use it consistently. (But if you pick some other style, and continue to have semicolon trouble, don't say I didn't warn you :-))

This is great advice.  However in a lot of real-world projects, more than one person has their hand in the "cookie jar".  For a project, what is really needed is coding standards.  Thus regardless of what prevalent standard is chosen, if a particular s/w developer (i.e. team member) is unwilling to adhere to the standard, well, then there is always the unemployment line to look forward to.

---

### Post by ofnuts on 2014-11-23
> **dwhitney67 said:**
> This is great advice.  However in a lot of real-world projects, more than one person has their hand in the "cookie jar".  For a project, what is really needed is coding standards.  Thus regardless of what prevalent standard is chosen, if a particular s/w developer (i.e. team member) is unwilling to adhere to the standard, well, then there is always the unemployment line to look forward to.

I have seen coding standards which would make the unemployment line look palatable. The first "professional" C coding rules I came across:

[LIST]
[*]use "#define BEGIN {" and "#define END }"
[*]no "switch" statements
[*]no compound assignment operators
[/LIST]
 
The project head was a Pascal fan (more accurately, his programming horizon was limited to Pascal).

---

