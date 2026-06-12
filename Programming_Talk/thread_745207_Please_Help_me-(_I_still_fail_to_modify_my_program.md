---
title: "Please Help me:-( I still fail to modify my program.:-("
date: 2008-04-04
forum: Programming Talk
---

### Post by ann pic on 2008-04-04
Help me..:-( I am now currently work hard to read image from my camera connected to capture card ( using PCI). I already try to modify the original source code below but i still cannot displayed anything. I want to use this program to read, capture image, and compress image snapped  it to JPEG. But still, i don't know what went wrong.. I modified it but when i compile my program still not sucess.. :-( Anyone could help me?



#include <stdio.h>
#include <stdlib.h>
#include <sys/ioctl.h>
#include <sys/mman.h>		// for munmap declarations
#include <linux/videodev.h>
#include <time.h>
#include <string.h>
#include <jpeglib.h>
#include <fcntl.h>
#include <errno.h>
#include <math.h>
#include <Imlib.h>
#include <jpeglib.h>
#define DEF_WIDTH	352
#define DEF_HEIGHT	288
/*-------------------------------------------
 * 
 *Variable/prototype below are used for capture engine
 *
 *-------------------------------------------*/
#define IN_TV			0
#define IN_COMPOSITE	1
#define IN_COMPOSITE2	2
#define IN_SVIDEO		3
#define IN_DEFAULT		8
#define NORM_PAL		0
#define NORM_NTSC		1
#define NORM_SECAM		2
#define NORM_DEFAULT	0 #define QUAL_DEFAULT	80	// jpeg quality factor 
char video_device[] = {"/dev/video0"};		// opened to read images via v4l
int dev;						// handle for v4l video camera device
struct video_picture v_pict;		// used to store prefered webcam palette 
 
int  v4l_open(char *device); void v4l_close(int dev); char *get_image(int dev,  int width, int height,                 int input,int norm,  int fmt, int *size); 
/*----------------------------------------------
 *
 *Array below are image buffer static declaration
 *
 *---------------------------------------------*/
static unsigned char rgb_buf[3*352*288];	// main 352x288 live display image buffer
static unsigned char ref_buf[3*352*288];        //temp reference picture buffer
static unsigned char pic_buf[3*352*288];        //temp analysis picture buffer
//put text on rgb variable char image_label[] = {"Lab  %Y-%m-%d %H:%M:%S"};// used by strftime to date stamp image
/*----------------------------------------------
 *
 *This variable are used in transform function
 *related to WaveletTransform.c files stuff
 *
 *---------------------------------------------*/
//wavelet variable expension
float *grayImage;
char *grayChar;//debug purpose
char *grayChar2; //debug purpose
float *waveletImage;
float *ref_waveImage;
//motion analysis variable int threshold = 30000;   //must more then 6000 at least for 18 noise level default=80000 morning int noiselevel = 18; //morning use not less then 15 night time use 4 office us 18 too int border = 5; //size of border thickness cut off from image int bottom_row = 60; //cut bottom row to avoid camera failure /* ----------------------------------------------------------------------
 * This routine extracted and modified from webcam project by Gerd Knorr
 * (c) 1998-2000 Gerd Knorr
 * Modified for colored text by L.P. Glaister July 2000
*/ 
# define CHAR_HEIGHT  11
# define CHAR_WIDTH   6
# define CHAR_START   4
# include "font_6x11.h"
void add_rgb_text(char *image, int width, int height, int alrm) {     time_t      t;     struct tm  *tm;     char        line[128],*ptr;     int         i,x,y,f,len;     time(&t);     tm = localtime(&t);    len = strftime(line,127,image_label,tm);
    for (y = 0; y < CHAR_HEIGHT; y++) 	{
		// locate text in lower left corner of image 	ptr = image + 3 * width * (height-CHAR_HEIGHT-2+y) + 12; 		// loop for each character in the string
	  	for (x = 0; x < len; x++)
		{
	    	// locate the character in the fontdata array 	f = fontdata[line[x] * CHAR_HEIGHT + y]; 			// loop for each column of font data 	    	for (i = CHAR_WIDTH-1; i >= 0; i--)
			{ 				// write a black background under text 				// comment out the following block to get white letters on picture background 	    		ptr[0] = 0; 	    		ptr[1] = 0; 		    	ptr[2] = 0; 				if (f & (CHAR_START << i)) 				{ 					if (alrm) 					{ 						// red text 		    			ptr[0] = 255; 		    			ptr[1] = 64; 		    			ptr[2] = 64; 					} 					else
					{ 						// white text 		    			ptr[0] = 255; 		    			ptr[1] = 255;
		    			ptr[2] = 255;
					} 				} 				ptr += 3;
	    	}
		}
    }
} //=====================================================================
// routine to convert to yuv image taking the Y value to bring to
// tranform() function for wavelet analysis
// 
//===================================================================== void tograyimage(unsigned char *img)
{
  int i; //grayImage=(float *) calloc(1,352*288*sizeof(float));   for(i=0;i<352*288;i++)
	grayImage[i] = (float) (0.3*img[3*i] +0.59*img[3*i+1] +0.11*img[3*i+2]); }
/*---------------------------------------------------------
 *main wavelet transform analysis call function from here
 *you need to add WaveletTransform.c file before compile
 *  *----------------------------------------------------------*/ void transform() {
  default_wavelet(); //called default value for wavelet HAAR coefficient
 //waveletImage = (float *)malloc(352*288*sizeof(float));   memcpy(waveletImage,grayImage,352*288*sizeof(float));   //call transform wavelet Haar Time with level 1   fwt(waveletImage,352,288,1);   hipass(waveletImage);   denoise(waveletImage,noiselevel);   ifwt(waveletImage,352,288,1);   //cut border frame   cut_border(waveletImage,border,352,288);   bot_cut(waveletImage,bottom_row,352,288); }
/*----------------------------------
 *
 *capture jpeg file with date
 *
 *--------------------------------*/ float capture_picture(void)
{
  time_t t;
  struct tm *tm;
  char line[128];   add_rgb_text(rgb_buf,DEF_WIDTH,DEF_HEIGHT, 0); //DEF_WIDTH = 352 and DEF_HEIGHT =288   time(&t);   tm = localtime(&t);   strftime(line, sizeof(line)-1,"ispy%H%M%S.jpg", tm);   put_picture(line, rgb_buf);   put_still_picture("motion.jpg",rgb_buf);     return 0.0; } 
void update_reference_image(void) {  static int first = 1;   if (first == 1)
    {
      first = 0; //ref_waveImage = (float *)malloc(352*288*sizeof(float));   	memcpy(ref_buf,rgb_buf,sizeof(ref_buf));
   	tograyimage(ref_buf);//filaname in grayscale float value is grayImage
   	transform(); //take grayImage to transform into waveletImage
   	memcpy(ref_waveImage,waveletImage,352*288*sizeof(float));    } } /*-----------------------------------------------
 *Do motion analysis using district wavelet transform
 *
 *
 *--------------------------------------------------*/
float do_motion_analysis(void)
{
  int i;
  int diff;
  long int sum=0;   /*declare variables */
  FILE *stream;
  int activated = 1;
  int deactivated = 0;   stream = fopen("ledlight.txt", "w");   fprintf(stream,"%d", deactivated); 
  fclose(stream);				/* close the file before ending program		*/   static int first = 1;   if (first == 1)
    {
      first = 0;
      return 0.0;
    } 
  tograyimage(pic_buf);   transform();   for(i=0; i<352*288; i++)
    {
      diff = abs(ref_waveImage[i] - waveletImage[i]);
      sum +=diff;
    }   printf("sum is %d\n",sum);
  if(sum>threshold)
    {       capture_picture();       stream = fopen("ledlight.txt", "w");       fprintf(stream,"%d", activated);        fclose(stream);     }   sum = 0;   return 0.0; } /* * read rgb image from v4l device
* return: mmap'ed buffer and size  *  * sample call:  *	int size;  *	char *image;  *  int dev = v4l_open(VIDEO_DEV, IN_DEFAULT);  *	image = get_image (dev, width, height, input, norm, palette, &size);  *	// process rgb image buffer as required here  *	// then dont forget to release buffers  *	if (size)  *		munmap(image, size);
 *	else if (image)
 *		free(image);  *  v4l_close(dev); */ 
char *get_image(int dev, int width, int height, int input,int norm,int fmt,int *size) { 	struct video_capability vid_caps; 	struct video_mbuf vid_buf; 	struct video_mmap vid_mmap; 	struct video_channel vid_chnl; 	char *map = NULL; 	int len;
	*size = 0;		// keep caller happy on error returns
	                // setting input = 1 gets some users going
	if (ioctl (dev, VIDIOCGCAP, &vid_caps) == -1)
	{ 		printf("ioctl (VIDIOCGCAP) failed\n"); 		return (NULL);
	} 	if (input != IN_DEFAULT) 	{ 		vid_chnl.channel = -1; 		if (ioctl (dev, VIDIOCGCHAN, &vid_chnl) == -1) 		{ 			printf("ioctl (VIDIOCGCHAN) failed\n"); 		} 		else 		{ 			vid_chnl.channel = input; 			vid_chnl.norm    = norm; 			if (ioctl (dev, VIDIOCSCHAN, &vid_chnl) == -1) 			{ 				printf("ioctl (VIDIOCSCHAN) failed"); 				return (NULL);
			} 		} 	}
	// if no video buffer set, then set it
	//printf("before VIDIOCGMBUF vidbuf size=%d bytes\n",vid_buf.size);
	if (ioctl (dev, VIDIOCGMBUF, &vid_buf) == -1)
	{ 		//printf("after VIDIOCGMBUF vidbuf size=%d bytes\n",vid_buf.size); 		// to do a normal read() 		map = malloc (width * height * 3); 		len = read (dev, map, width * height * 3); 		if (len <=  0) 		{ 			free (map); 			return (NULL); 		} 		*size = 0;
		return (map); 	}
	//most probalbly be using this method MIMO 	map = mmap (0, vid_buf.size, PROT_READ|PROT_WRITE,MAP_SHARED,dev,0);
	if ((unsigned char *)-1 == (unsigned char *)map)
	{
		printf("mmap() failed \n");                 	return (NULL); 	} 	vid_mmap.format = fmt;      //video format refer V4L documentation
	vid_mmap.frame = 0;         //usually sets to zero 
	vid_mmap.width = width;     //set capability of webcam drivers
	vid_mmap.height =height; 	printf("VIDIOCMCAPTURE started\n"); 	if (ioctl (dev, VIDIOCMCAPTURE, &vid_mmap) == -1) 	{
		printf("VIDIOCMCAPTURE failed\n");
		munmap (map, vid_buf.size);
		return (NULL);
	} 	printf("VIDIOCSYNC started\n"); 	if (ioctl (dev, VIDIOCSYNC, &vid_mmap) == -1)
	{
		printf("VIDIOCSYNC failed \n");
		munmap (map, vid_buf.size);
		return (NULL);
	} 	printf("VIDIOCSYNC finished %d bytes\n",vid_buf.size);
	// vid_buf.size is actually the size of 2 frame buffers in the driver
	*size = vid_buf.size;
	return (map); } /*
 *  int v4l_open(char *device) *	example call  int dev = v4l_open(VIDEO_DEV)
 *
 *
 */ int v4l_open(char *device)
{ 	int dev = -1; 	int max_try = 5;	/* we try 5 seconds/times to open the device */ 	/* open the video4linux device */ 	while (max_try) 	{ 		dev = open (device, O_RDWR); 		if (dev == -1) 		{ 			if (!--max_try) 			{ 				fprintf (stderr, "Can't open device %s\n", device); 				exit (0); 			} 			sleep (1); 		} 		else
		{ 			break; 		}
	}
	return dev; } /*
 *  void v4l_close(int dev)
 *	example call  v4l_close(dev);
 *  */ void v4l_close(int dev) { 	if (dev > 0) 		close(dev);
} int main( int argc, char *argv[] ) {   	int size;
	char *image;
	char *picture;
	char tmp;
	char *img_ptr;
	int cnt; 	int counter = 0; //for testbench uses!!     // used to store supported webcam palette mode
    struct video_picture v_pict; 	v_pict.palette=0;					// mark supported palette unknown 	dev = v4l_open(video_device);		// open the camera device 	if (dev <= 0) 	{ 		printf("Unable to use v4l camera device... open failed???"); 		return 0;
	} 	if(!v_pict.palette) 	{
		// get palette info
		if(ioctl(dev, VIDIOCGPICT, &v_pict)==-1)
		{ 			printf("Unable to get picture properties from webcam (VIDIOCGPICT failed)\n");
			return 0;
		}
		if(v_pict.palette!=VIDEO_PALETTE_YUV420P && v_pict.palette!=VIDEO_PALETTE_RGB24)
		{ 			// try to switch to RGB24 palette 			v_pict.palette=VIDEO_PALETTE_RGB24;
			if(ioctl(dev, VIDIOCSPICT, &v_pict)==-1)
			{ 			printf("RGB24 not supported, trying YUV420P...\n"); 			return 0; 			} 		}
	}
	//before entering loop grayImage=(float *) calloc(1,352*288*sizeof(float));
waveletImage = (float *)malloc(352*288*sizeof(float));
ref_waveImage = (float *)malloc(352*288*sizeof(float));
    for (;;)     {
        //grab a v4l frame 	    image = get_image(dev,DEF_WIDTH,DEF_HEIGHT,IN_DEFAULT,NORM_NTSC,v_pict.palette,&size);    	    if ( image )
	    {
	      //BGR24 palette format 	      // grab a static memory copy for use in calcs and redraws
	      memcpy(rgb_buf,image,sizeof(rgb_buf));
	      memcpy(pic_buf,rgb_buf,sizeof(pic_buf)); //for anaylsis grayscale
	      // v4l returns bgr not rgb, so we need to swap red and blue 	      // for our display 	      img_ptr = rgb_buf; 	      for (cnt=0; cnt < 352*288; cnt++) 		{
		  tmp = img_ptr[0];			// get blue for safe keeping 
		img_ptr[0] = img_ptr[2];	// move red into correct place   img_ptr[2] = tmp;			// park blue in correct place 		  img_ptr += 3;				// bump to next triplet
		}
	    } 	    else
		    printf("image capture failed\n"); 	    // then release buffers which has been used
	    if (size)
    	    munmap(image, size);
	    else
	    if (image)
    	    free(image); 	    //algothrim start here 	    do_motion_analysis(); 	    //printf("counter = %d \n",counter); 	    update_reference_image(); 	    //counter++;     } }

---

### Post by Wybiral on 2008-04-04
The problem seems to be that your code has smilies in it... That can't be good. :)

PS: Post code using the [ code ] [ / code ] tags.

---

### Post by ann pic on 2008-04-04
i am new to ubuntu forum..: -( ..Help me

```

#include <stdio.h>
#include <stdlib.h>
#include <sys/ioctl.h>
#include <sys/mman.h>		// for munmap declarations
#include <linux/videodev.h>
#include <time.h>
#include <string.h>
#include <jpeglib.h>
#include <fcntl.h>
#include <errno.h>
#include <math.h>
#include <Imlib.h>
#include <jpeglib.h>
#define DEF_WIDTH	352
#define DEF_HEIGHT	288
/*-------------------------------------------
 * 
 *Variable/prototype below are used for capture engine
 *
 *-------------------------------------------*/
#define IN_TV			0
#define IN_COMPOSITE	1
#define IN_COMPOSITE2	2
#define IN_SVIDEO		3
#define IN_DEFAULT		8
#define NORM_PAL		0
#define NORM_NTSC		1
#define NORM_SECAM		2
#define NORM_DEFAULT	0 #define QUAL_DEFAULT	80	// jpeg quality factor 
char video_device[] = {"/dev/video0"};		// opened to read images via v4l
int dev;						// handle for v4l video camera device
struct video_picture v_pict;		// used to store prefered webcam palette 
 
int  v4l_open(char *device); void v4l_close(int dev); char *get_image(int dev,  int width, int height,                 int input,int norm,  int fmt, int *size); 
/*----------------------------------------------
 *
 *Array below are image buffer static declaration
 *
 *---------------------------------------------*/
static unsigned char rgb_buf[3*352*288];	// main 352x288 live display image buffer
static unsigned char ref_buf[3*352*288];        //temp reference picture buffer
static unsigned char pic_buf[3*352*288];        //temp analysis picture buffer
//put text on rgb variable char image_label[] = {"Lab  %Y-%m-%d %H:%M:%S"};// used by strftime to date stamp image
/*----------------------------------------------
 *
 *This variable are used in transform function
 *related to WaveletTransform.c files stuff
 *
 *---------------------------------------------*/
//wavelet variable expension
float *grayImage;
char *grayChar;//debug purpose
char *grayChar2; //debug purpose
float *waveletImage;
float *ref_waveImage;
//motion analysis variable int threshold = 30000;   //must more then 6000 at least for 18 noise level default=80000 morning int noiselevel = 18; //morning use not less then 15 night time use 4 office us 18 too int border = 5; //size of border thickness cut off from image int bottom_row = 60; //cut bottom row to avoid camera failure /* ----------------------------------------------------------------------
 * This routine extracted and modified from webcam project by Gerd Knorr
 * (c) 1998-2000 Gerd Knorr
 * Modified for colored text by L.P. Glaister July 2000
*/ 
# define CHAR_HEIGHT  11
# define CHAR_WIDTH   6
# define CHAR_START   4
# include "font_6x11.h"
void add_rgb_text(char *image, int width, int height, int alrm) {     time_t      t;     struct tm  *tm;     char        line[128],*ptr;     int         i,x,y,f,len;     time(&t);     tm = localtime(&t);    len = strftime(line,127,image_label,tm);
    for (y = 0; y < CHAR_HEIGHT; y++) 	{
		// locate text in lower left corner of image 	ptr = image + 3 * width * (height-CHAR_HEIGHT-2+y) + 12; 		// loop for each character in the string
	  	for (x = 0; x < len; x++)
		{
	    	// locate the character in the fontdata array 	f = fontdata[line[x] * CHAR_HEIGHT + y]; 			// loop for each column of font data 	    	for (i = CHAR_WIDTH-1; i >= 0; i--)
			{ 				// write a black background under text 				// comment out the following block to get white letters on picture background 	    		ptr[0] = 0; 	    		ptr[1] = 0; 		    	ptr[2] = 0; 				if (f & (CHAR_START << i)) 				{ 					if (alrm) 					{ 						// red text 		    			ptr[0] = 255; 		    			ptr[1] = 64; 		    			ptr[2] = 64; 					} 					else
					{ 						// white text 		    			ptr[0] = 255; 		    			ptr[1] = 255;
		    			ptr[2] = 255;
					} 				} 				ptr += 3;
	    	}
		}
    }
} //=====================================================================
// routine to convert to yuv image taking the Y value to bring to
// tranform() function for wavelet analysis
// 
//===================================================================== void tograyimage(unsigned char *img)
{
  int i; //grayImage=(float *) calloc(1,352*288*sizeof(float));   for(i=0;i<352*288;i++)
	grayImage[i] = (float) (0.3*img[3*i] +0.59*img[3*i+1] +0.11*img[3*i+2]); }
/*---------------------------------------------------------
 *main wavelet transform analysis call function from here
 *you need to add WaveletTransform.c file before compile
 *  *----------------------------------------------------------*/ void transform() {
  default_wavelet(); //called default value for wavelet HAAR coefficient
 //waveletImage = (float *)malloc(352*288*sizeof(float));   memcpy(waveletImage,grayImage,352*288*sizeof(float));   //call transform wavelet Haar Time with level 1   fwt(waveletImage,352,288,1);   hipass(waveletImage);   denoise(waveletImage,noiselevel);   ifwt(waveletImage,352,288,1);   //cut border frame   cut_border(waveletImage,border,352,288);   bot_cut(waveletImage,bottom_row,352,288); }
/*----------------------------------
 *
 *capture jpeg file with date
 *
 *--------------------------------*/ float capture_picture(void)
{
  time_t t;
  struct tm *tm;
  char line[128];   add_rgb_text(rgb_buf,DEF_WIDTH,DEF_HEIGHT, 0); //DEF_WIDTH = 352 and DEF_HEIGHT =288   time(&t);   tm = localtime(&t);   strftime(line, sizeof(line)-1,"ispy%H%M%S.jpg", tm);   put_picture(line, rgb_buf);   put_still_picture("motion.jpg",rgb_buf);     return 0.0; } 
void update_reference_image(void) {  static int first = 1;   if (first == 1)
    {
      first = 0; //ref_waveImage = (float *)malloc(352*288*sizeof(float));   	memcpy(ref_buf,rgb_buf,sizeof(ref_buf));
   	tograyimage(ref_buf);//filaname in grayscale float value is grayImage
   	transform(); //take grayImage to transform into waveletImage
   	memcpy(ref_waveImage,waveletImage,352*288*sizeof(float));    } } /*-----------------------------------------------
 *Do motion analysis using district wavelet transform
 *
 *
 *--------------------------------------------------*/
float do_motion_analysis(void)
{
  int i;
  int diff;
  long int sum=0;   /*declare variables */
  FILE *stream;
  int activated = 1;
  int deactivated = 0;   stream = fopen("ledlight.txt", "w");   fprintf(stream,"%d", deactivated); 
  fclose(stream);				/* close the file before ending program		*/   static int first = 1;   if (first == 1)
    {
      first = 0;
      return 0.0;
    } 
  tograyimage(pic_buf);   transform();   for(i=0; i<352*288; i++)
    {
      diff = abs(ref_waveImage[i] - waveletImage[i]);
      sum +=diff;
    }   printf("sum is %d\n",sum);
  if(sum>threshold)
    {       capture_picture();       stream = fopen("ledlight.txt", "w");       fprintf(stream,"%d", activated);        fclose(stream);     }   sum = 0;   return 0.0; } /* * read rgb image from v4l device
* return: mmap'ed buffer and size  *  * sample call:  *	int size;  *	char *image;  *  int dev = v4l_open(VIDEO_DEV, IN_DEFAULT);  *	image = get_image (dev, width, height, input, norm, palette, &size);  *	// process rgb image buffer as required here  *	// then dont forget to release buffers  *	if (size)  *		munmap(image, size);
 *	else if (image)
 *		free(image);  *  v4l_close(dev); */ 
char *get_image(int dev, int width, int height, int input,int norm,int fmt,int *size) { 	struct video_capability vid_caps; 	struct video_mbuf vid_buf; 	struct video_mmap vid_mmap; 	struct video_channel vid_chnl; 	char *map = NULL; 	int len;
	*size = 0;		// keep caller happy on error returns
	                // setting input = 1 gets some users going
	if (ioctl (dev, VIDIOCGCAP, &vid_caps) == -1)
	{ 		printf("ioctl (VIDIOCGCAP) failed\n"); 		return (NULL);
	} 	if (input != IN_DEFAULT) 	{ 		vid_chnl.channel = -1; 		if (ioctl (dev, VIDIOCGCHAN, &vid_chnl) == -1) 		{ 			printf("ioctl (VIDIOCGCHAN) failed\n"); 		} 		else 		{ 			vid_chnl.channel = input; 			vid_chnl.norm    = norm; 			if (ioctl (dev, VIDIOCSCHAN, &vid_chnl) == -1) 			{ 				printf("ioctl (VIDIOCSCHAN) failed"); 				return (NULL);
			} 		} 	}
	// if no video buffer set, then set it
	//printf("before VIDIOCGMBUF vidbuf size=%d bytes\n",vid_buf.size);
	if (ioctl (dev, VIDIOCGMBUF, &vid_buf) == -1)
	{ 		//printf("after VIDIOCGMBUF vidbuf size=%d bytes\n",vid_buf.size); 		// to do a normal read() 		map = malloc (width * height * 3); 		len = read (dev, map, width * height * 3); 		if (len <=  0) 		{ 			free (map); 			return (NULL); 		} 		*size = 0;
		return (map); 	}
	//most probalbly be using this method MIMO 	map = mmap (0, vid_buf.size, PROT_READ|PROT_WRITE,MAP_SHARED,dev,0);
	if ((unsigned char *)-1 == (unsigned char *)map)
	{
		printf("mmap() failed \n");                 	return (NULL); 	} 	vid_mmap.format = fmt;      //video format refer V4L documentation
	vid_mmap.frame = 0;         //usually sets to zero 
	vid_mmap.width = width;     //set capability of webcam drivers
	vid_mmap.height =height; 	printf("VIDIOCMCAPTURE started\n"); 	if (ioctl (dev, VIDIOCMCAPTURE, &vid_mmap) == -1) 	{
		printf("VIDIOCMCAPTURE failed\n");
		munmap (map, vid_buf.size);
		return (NULL);
	} 	printf("VIDIOCSYNC started\n"); 	if (ioctl (dev, VIDIOCSYNC, &vid_mmap) == -1)
	{
		printf("VIDIOCSYNC failed \n");
		munmap (map, vid_buf.size);
		return (NULL);
	} 	printf("VIDIOCSYNC finished %d bytes\n",vid_buf.size);
	// vid_buf.size is actually the size of 2 frame buffers in the driver
	*size = vid_buf.size;
	return (map); } /*
 *  int v4l_open(char *device) *	example call  int dev = v4l_open(VIDEO_DEV)
 *
 *
 */ int v4l_open(char *device)
{ 	int dev = -1; 	int max_try = 5;	/* we try 5 seconds/times to open the device */ 	/* open the video4linux device */ 	while (max_try) 	{ 		dev = open (device, O_RDWR); 		if (dev == -1) 		{ 			if (!--max_try) 			{ 				fprintf (stderr, "Can't open device %s\n", device); 				exit (0); 			} 			sleep (1); 		} 		else
		{ 			break; 		}
	}
	return dev; } /*
 *  void v4l_close(int dev)
 *	example call  v4l_close(dev);
 *  */ void v4l_close(int dev) { 	if (dev > 0) 		close(dev);
} int main( int argc, char *argv[] ) {   	int size;
	char *image;
	char *picture;
	char tmp;
	char *img_ptr;
	int cnt; 	int counter = 0; //for testbench uses!!     // used to store supported webcam palette mode
    struct video_picture v_pict; 	v_pict.palette=0;					// mark supported palette unknown 	dev = v4l_open(video_device);		// open the camera device 	if (dev <= 0) 	{ 		printf("Unable to use v4l camera device... open failed???"); 		return 0;
	} 	if(!v_pict.palette) 	{
		// get palette info
		if(ioctl(dev, VIDIOCGPICT, &v_pict)==-1)
		{ 			printf("Unable to get picture properties from webcam (VIDIOCGPICT failed)\n");
			return 0;
		}
		if(v_pict.palette!=VIDEO_PALETTE_YUV420P && v_pict.palette!=VIDEO_PALETTE_RGB24)
		{ 			// try to switch to RGB24 palette 			v_pict.palette=VIDEO_PALETTE_RGB24;
			if(ioctl(dev, VIDIOCSPICT, &v_pict)==-1)
			{ 			printf("RGB24 not supported, trying YUV420P...\n"); 			return 0; 			} 		}
	}
	//before entering loop grayImage=(float *) calloc(1,352*288*sizeof(float));
waveletImage = (float *)malloc(352*288*sizeof(float));
ref_waveImage = (float *)malloc(352*288*sizeof(float));
    for (;;)     {
        //grab a v4l frame 	    image = get_image(dev,DEF_WIDTH,DEF_HEIGHT,IN_DEFAULT,NORM_NTSC,v_pict.palette,&size);    	    if ( image )
	    {
	      //BGR24 palette format 	      // grab a static memory copy for use in calcs and redraws
	      memcpy(rgb_buf,image,sizeof(rgb_buf));
	      memcpy(pic_buf,rgb_buf,sizeof(pic_buf)); //for anaylsis grayscale
	      // v4l returns bgr not rgb, so we need to swap red and blue 	      // for our display 	      img_ptr = rgb_buf; 	      for (cnt=0; cnt < 352*288; cnt++) 		{
		  tmp = img_ptr[0];			// get blue for safe keeping 
		img_ptr[0] = img_ptr[2];	// move red into correct place   img_ptr[2] = tmp;			// park blue in correct place 		  img_ptr += 3;				// bump to next triplet
		}
	    } 	    else
		    printf("image capture failed\n"); 	    // then release buffers which has been used
	    if (size)
    	    munmap(image, size);
	    else
	    if (image)
    	    free(image); 	    //algothrim start here 	    do_motion_analysis(); 	    //printf("counter = %d \n",counter); 	    update_reference_image(); 	    //counter++;     } }

```

---

### Post by ann pic on 2008-04-04
```

#include <stdio.h>
#include <stdlib.h>
#include <sys/ioctl.h>
#include <sys/mman.h>		// for munmap declarations
#include <linux/videodev.h>
#include <time.h>
#include <string.h>
#include <jpeglib.h>
#include <fcntl.h>
#include <errno.h>
#include <math.h>
#include <Imlib.h>
#include <jpeglib.h>
#define DEF_WIDTH	352
#define DEF_HEIGHT	288
/*-------------------------------------------
 * 
 *Variable/prototype below are used for capture engine
 *
 *-------------------------------------------*/
#define IN_TV			0
#define IN_COMPOSITE	1
#define IN_COMPOSITE2	2
#define IN_SVIDEO		3
#define IN_DEFAULT		8
#define NORM_PAL		0
#define NORM_NTSC		1
#define NORM_SECAM		2
#define NORM_DEFAULT	0 #define QUAL_DEFAULT	80	// jpeg quality factor 
char video_device[] = {"/dev/video0"};		// opened to read images via v4l
int dev;						// handle for v4l video camera device
struct video_picture v_pict;		// used to store prefered webcam palette 
 
int  v4l_open(char *device); void v4l_close(int dev); char *get_image(int dev,  int width, int height,                 int input,int norm,  int fmt, int *size); 
/*----------------------------------------------
 *
 *Array below are image buffer static declaration
 *
 *---------------------------------------------*/
static unsigned char rgb_buf[3*352*288];	// main 352x288 live display image buffer
static unsigned char ref_buf[3*352*288];        //temp reference picture buffer
static unsigned char pic_buf[3*352*288];        //temp analysis picture buffer
//put text on rgb variable char image_label[] = {"Lab  %Y-%m-%d %H:%M:%S"};// used by strftime to date stamp image
/*----------------------------------------------
 *
 *This variable are used in transform function
 *related to WaveletTransform.c files stuff
 *
 *---------------------------------------------*/
//wavelet variable expension
float *grayImage;
char *grayChar;//debug purpose
char *grayChar2; //debug purpose
float *waveletImage;
float *ref_waveImage;
//motion analysis variable int threshold = 30000;   //must more then 6000 at least for 18 noise level default=80000 morning int noiselevel = 18; //morning use not less then 15 night time use 4 office us 18 too int border = 5; //size of border thickness cut off from image int bottom_row = 60; //cut bottom row to avoid camera failure /* ----------------------------------------------------------------------
 * This routine extracted and modified from webcam project by Gerd Knorr
 * (c) 1998-2000 Gerd Knorr
 * Modified for colored text by L.P. Glaister July 2000
*/ 
# define CHAR_HEIGHT  11
# define CHAR_WIDTH   6
# define CHAR_START   4
# include "font_6x11.h"
void add_rgb_text(char *image, int width, int height, int alrm) {     time_t      t;     struct tm  *tm;     char        line[128],*ptr;     int         i,x,y,f,len;     time(&t);     tm = localtime(&t);    len = strftime(line,127,image_label,tm);
    for (y = 0; y < CHAR_HEIGHT; y++) 	{
		// locate text in lower left corner of image 	ptr = image + 3 * width * (height-CHAR_HEIGHT-2+y) + 12; 		// loop for each character in the string
	  	for (x = 0; x < len; x++)
		{
	    	// locate the character in the fontdata array 	f = fontdata[line[x] * CHAR_HEIGHT + y]; 			// loop for each column of font data 	    	for (i = CHAR_WIDTH-1; i >= 0; i--)
			{ 				// write a black background under text 				// comment out the following block to get white letters on picture background 	    		ptr[0] = 0; 	    		ptr[1] = 0; 		    	ptr[2] = 0; 				if (f & (CHAR_START << i)) 				{ 					if (alrm) 					{ 						// red text 		    			ptr[0] = 255; 		    			ptr[1] = 64; 		    			ptr[2] = 64; 					} 					else
					{ 						// white text 		    			ptr[0] = 255; 		    			ptr[1] = 255;
		    			ptr[2] = 255;
					} 				} 				ptr += 3;
	    	}
		}
    }
} //=====================================================================
// routine to convert to yuv image taking the Y value to bring to
// tranform() function for wavelet analysis
// 
//===================================================================== void tograyimage(unsigned char *img)
{
  int i; //grayImage=(float *) calloc(1,352*288*sizeof(float));   for(i=0;i<352*288;i++)
	grayImage[i] = (float) (0.3*img[3*i] +0.59*img[3*i+1] +0.11*img[3*i+2]); }
/*---------------------------------------------------------
 *main wavelet transform analysis call function from here
 *you need to add WaveletTransform.c file before compile
 *  *----------------------------------------------------------*/ void transform() {
  default_wavelet(); //called default value for wavelet HAAR coefficient
 //waveletImage = (float *)malloc(352*288*sizeof(float));   memcpy(waveletImage,grayImage,352*288*sizeof(float));   //call transform wavelet Haar Time with level 1   fwt(waveletImage,352,288,1);   hipass(waveletImage);   denoise(waveletImage,noiselevel);   ifwt(waveletImage,352,288,1);   //cut border frame   cut_border(waveletImage,border,352,288);   bot_cut(waveletImage,bottom_row,352,288); }
/*----------------------------------
 *
 *capture jpeg file with date
 *
 *--------------------------------*/ float capture_picture(void)
{
  time_t t;
  struct tm *tm;
  char line[128];   add_rgb_text(rgb_buf,DEF_WIDTH,DEF_HEIGHT, 0); //DEF_WIDTH = 352 and DEF_HEIGHT =288   time(&t);   tm = localtime(&t);   strftime(line, sizeof(line)-1,"ispy%H%M%S.jpg", tm);   put_picture(line, rgb_buf);   put_still_picture("motion.jpg",rgb_buf);     return 0.0; } 
void update_reference_image(void) {  static int first = 1;   if (first == 1)
    {
      first = 0; //ref_waveImage = (float *)malloc(352*288*sizeof(float));   	memcpy(ref_buf,rgb_buf,sizeof(ref_buf));
   	tograyimage(ref_buf);//filaname in grayscale float value is grayImage
   	transform(); //take grayImage to transform into waveletImage
   	memcpy(ref_waveImage,waveletImage,352*288*sizeof(float));    } } /*-----------------------------------------------
 *Do motion analysis using district wavelet transform
 *
 *
 *--------------------------------------------------*/
float do_motion_analysis(void)
{
  int i;
  int diff;
  long int sum=0;   /*declare variables */
  FILE *stream;
  int activated = 1;
  int deactivated = 0;   stream = fopen("ledlight.txt", "w");   fprintf(stream,"%d", deactivated); 
  fclose(stream);				/* close the file before ending program		*/   static int first = 1;   if (first == 1)
    {
      first = 0;
      return 0.0;
    } 
  tograyimage(pic_buf);   transform();   for(i=0; i<352*288; i++)
    {
      diff = abs(ref_waveImage[i] - waveletImage[i]);
      sum +=diff;
    }   printf("sum is %d\n",sum);
  if(sum>threshold)
    {       capture_picture();       stream = fopen("ledlight.txt", "w");       fprintf(stream,"%d", activated);        fclose(stream);     }   sum = 0;   return 0.0; } /* * read rgb image from v4l device
* return: mmap'ed buffer and size  *  * sample call:  *	int size;  *	char *image;  *  int dev = v4l_open(VIDEO_DEV, IN_DEFAULT);  *	image = get_image (dev, width, height, input, norm, palette, &size);  *	// process rgb image buffer as required here  *	// then dont forget to release buffers  *	if (size)  *		munmap(image, size);
 *	else if (image)
 *		free(image);  *  v4l_close(dev); */ 
char *get_image(int dev, int width, int height, int input,int norm,int fmt,int *size) { 	struct video_capability vid_caps; 	struct video_mbuf vid_buf; 	struct video_mmap vid_mmap; 	struct video_channel vid_chnl; 	char *map = NULL; 	int len;
	*size = 0;		// keep caller happy on error returns
	                // setting input = 1 gets some users going
	if (ioctl (dev, VIDIOCGCAP, &vid_caps) == -1)
	{ 		printf("ioctl (VIDIOCGCAP) failed\n"); 		return (NULL);
	} 	if (input != IN_DEFAULT) 	{ 		vid_chnl.channel = -1; 		if (ioctl (dev, VIDIOCGCHAN, &vid_chnl) == -1) 		{ 			printf("ioctl (VIDIOCGCHAN) failed\n"); 		} 		else 		{ 			vid_chnl.channel = input; 			vid_chnl.norm    = norm; 			if (ioctl (dev, VIDIOCSCHAN, &vid_chnl) == -1) 			{ 				printf("ioctl (VIDIOCSCHAN) failed"); 				return (NULL);
			} 		} 	}
	// if no video buffer set, then set it
	//printf("before VIDIOCGMBUF vidbuf size=%d bytes\n",vid_buf.size);
	if (ioctl (dev, VIDIOCGMBUF, &vid_buf) == -1)
	{ 		//printf("after VIDIOCGMBUF vidbuf size=%d bytes\n",vid_buf.size); 		// to do a normal read() 		map = malloc (width * height * 3); 		len = read (dev, map, width * height * 3); 		if (len <=  0) 		{ 			free (map); 			return (NULL); 		} 		*size = 0;
		return (map); 	}
	//most probalbly be using this method MIMO 	map = mmap (0, vid_buf.size, PROT_READ|PROT_WRITE,MAP_SHARED,dev,0);
	if ((unsigned char *)-1 == (unsigned char *)map)
	{
		printf("mmap() failed \n");                 	return (NULL); 	} 	vid_mmap.format = fmt;      //video format refer V4L documentation
	vid_mmap.frame = 0;         //usually sets to zero 
	vid_mmap.width = width;     //set capability of webcam drivers
	vid_mmap.height =height; 	printf("VIDIOCMCAPTURE started\n"); 	if (ioctl (dev, VIDIOCMCAPTURE, &vid_mmap) == -1) 	{
		printf("VIDIOCMCAPTURE failed\n");
		munmap (map, vid_buf.size);
		return (NULL);
	} 	printf("VIDIOCSYNC started\n"); 	if (ioctl (dev, VIDIOCSYNC, &vid_mmap) == -1)
	{
		printf("VIDIOCSYNC failed \n");
		munmap (map, vid_buf.size);
		return (NULL);
	} 	printf("VIDIOCSYNC finished %d bytes\n",vid_buf.size);
	// vid_buf.size is actually the size of 2 frame buffers in the driver
	*size = vid_buf.size;
	return (map); } /*
 *  int v4l_open(char *device) *	example call  int dev = v4l_open(VIDEO_DEV)
 *
 *
 */ int v4l_open(char *device)
{ 	int dev = -1; 	int max_try = 5;	/* we try 5 seconds/times to open the device */ 	/* open the video4linux device */ 	while (max_try) 	{ 		dev = open (device, O_RDWR); 		if (dev == -1) 		{ 			if (!--max_try) 			{ 				fprintf (stderr, "Can't open device %s\n", device); 				exit (0); 			} 			sleep (1); 		} 		else
		{ 			break; 		}
	}
	return dev; } /*
 *  void v4l_close(int dev)
 *	example call  v4l_close(dev);
 *  */ void v4l_close(int dev) { 	if (dev > 0) 		close(dev);
} int main( int argc, char *argv[] ) {   	int size;
	char *image;
	char *picture;
	char tmp;
	char *img_ptr;
	int cnt; 	int counter = 0; //for testbench uses!!     // used to store supported webcam palette mode
    struct video_picture v_pict; 	v_pict.palette=0;					// mark supported palette unknown 	dev = v4l_open(video_device);		// open the camera device 	if (dev <= 0) 	{ 		printf("Unable to use v4l camera device... open failed???"); 		return 0;
	} 	if(!v_pict.palette) 	{
		// get palette info
		if(ioctl(dev, VIDIOCGPICT, &v_pict)==-1)
		{ 			printf("Unable to get picture properties from webcam (VIDIOCGPICT failed)\n");
			return 0;
		}
		if(v_pict.palette!=VIDEO_PALETTE_YUV420P && v_pict.palette!=VIDEO_PALETTE_RGB24)
		{ 			// try to switch to RGB24 palette 			v_pict.palette=VIDEO_PALETTE_RGB24;
			if(ioctl(dev, VIDIOCSPICT, &v_pict)==-1)
			{ 			printf("RGB24 not supported, trying YUV420P...\n"); 			return 0; 			} 		}
	}
	//before entering loop grayImage=(float *) calloc(1,352*288*sizeof(float));
waveletImage = (float *)malloc(352*288*sizeof(float));
ref_waveImage = (float *)malloc(352*288*sizeof(float));
    for (;;)     {
        //grab a v4l frame 	    image = get_image(dev,DEF_WIDTH,DEF_HEIGHT,IN_DEFAULT,NORM_NTSC,v_pict.palette,&size);    	    if ( image )
	    {
	      //BGR24 palette format 	      // grab a static memory copy for use in calcs and redraws
	      memcpy(rgb_buf,image,sizeof(rgb_buf));
	      memcpy(pic_buf,rgb_buf,sizeof(pic_buf)); //for anaylsis grayscale
	      // v4l returns bgr not rgb, so we need to swap red and blue 	      // for our display 	      img_ptr = rgb_buf; 	      for (cnt=0; cnt < 352*288; cnt++) 		{
		  tmp = img_ptr[0];			// get blue for safe keeping 
		img_ptr[0] = img_ptr[2];	// move red into correct place   img_ptr[2] = tmp;			// park blue in correct place 		  img_ptr += 3;				// bump to next triplet
		}
	    } 	    else
		    printf("image capture failed\n"); 	    // then release buffers which has been used
	    if (size)
    	    munmap(image, size);
	    else
	    if (image)
    	    free(image); 	    //algothrim start here 	    do_motion_analysis(); 	    //printf("counter = %d \n",counter); 	    update_reference_image(); 	    //counter++;     } }

```

---

### Post by mike_g on 2008-04-04
Ok, well maybe you could explain what you altered that broke the program? 

Also, if you want people to go over your code you might want to fix your indentation.

---

### Post by ann pic on 2008-04-04
This source code is use with webcam camera, but in my case i am using Video Capture card connected to my analogue camera (BNC to RCA connector) to display my picture. I want to read image snapped from my camera. But then i already try to modify this program, but when i compile i got warnings and errors.

---

### Post by Zugzwang on 2008-04-04
Ok, try to compile the original program first.

If it compiles, tell use what you modified and copy&paste the compiler errors here.

---

### Post by smartbei on 2008-04-04
Check the last line of the code you pasted - it looks like two curly brackets were added to the comment by mistake. Go through the rest of the code. there are other places where it appears that code was added to the comments.

---

### Post by ann pic on 2008-04-04
i can compile it but i cannot display anything.  Because i am using PCI capture card. I am not using webcam.  When i execute the program in the terminal it will display the output as below.

```

VIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 
VIDIOCSYNC started 
^AVIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 
VIDIOCSYNC started 
VIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 
VIDIOCSYNC started 
VIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 
VIDIOCSYNC started 
VIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 
VIDIOCSYNC started 
VIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 
VIDIOCSYNC started 
VIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 
VIDIOCSYNC started 
VIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 
VIDIOCSYNC started 
VIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 
VIDIOCSYNC started 
VIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 
VIDIOCSYNC started 
VIDIOCSYNC finished 17039360 bytes 
sum is 0 
VIDIOCMCAPTURE started 

```

it will continuously run in the terminal like that only. I want to display image.. :-( I already try to modify the program so that it can read image from camera..

---

