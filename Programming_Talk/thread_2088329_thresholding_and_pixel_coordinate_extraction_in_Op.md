---
title: "thresholding and pixel coordinate extraction in OpenCV"
date: 2012-11-26
forum: Programming Talk
---

### Post by rasmus91 on 2012-11-26
Hi everyone.

Im currently using OpenCV for a project at school, and we are not supposed to use the already builtin thresholding function, as that would be too easy i assume.

Im trying to do two things; perform thresholding, and to fill an array with all x-coordinates, and another with the y-coordinates, for object pixels. it doesn't work however, and i do not understand why.

here my code:
```
#include <iostream>
#include <string>
#include <opencv2/core/core.hpp>
#include <opencv2/highgui/highgui.hpp>
#include <opencv2/imgproc/imgproc.hpp>

using namespace std;
using namespace cv;

Mat blobDetection(Mat binaryIMG){ //function to do objectextraction
int binaryIMG_Height = binaryIMG.rows, binaryIMG_Width = binaryIMG.cols, pixValue, blobSize = 0, objectSize = 0;
Mat objectImage;

//find the amount of object pixels (white)
for(int x = 0; x < binaryIMG_Width; x++){
    for(int y = 0; y < binaryIMG_Height; y++){
    pixValue = binaryIMG.at<unsigned char>(x,y);
    if(pixValue > 0){
    blobSize++;
    }
    }
}

// initialize arrays for holding coordinate values
int blobXCoordinates[blobSize], blobYCoordinates[blobSize];

//fill in the coordinate values
for(int x = 0; x < binaryIMG_Width; x++){
    int i = 0;
    int xCoordinate, yCoordinate;
    for(int y = 0; y < binaryIMG_Height; y++){
    pixValue = binaryIMG.at<unsigned char>(x,y);
    if(pixValue == 255){
    blobXCoordinates[i] = x;
    blobYCoordinates[i] = y;
    i++;
    }
    }
}

for(int cycle = 0; cycle <= blobSize; cycle++){
cout << blobXCoordinates[cycle] << " " << blobYCoordinates[cycle] << endl;
}

//should ideally return these values
}

Mat thresholdIMG(Mat inputImg, int lowerValue, int highValue){
int width = inputImg.cols, height = inputImg.rows, pixValue;
Mat outputImg;

//thresholding function to set all pixl values to either 0 or 255 dependant on the threshold values set
for(int x = 0; x <= width; x++){
    for(int y = 0; y <= height; y++){
    pixValue = inputImg.at<unsigned char>(x,y);
    if(pixValue >= lowerValue && pixValue <= highValue){
    outputImg.at<unsigned char>(x,y) = 255;
    }else{
    outputImg.at<unsigned char>(x,y) = 0;
    }
    }

}
return outputImg;

}

int main(int argc, char** argv)
{
    VideoCapture capture;

    if (argc == 2)
        capture.open(argv[1]);
    else
        capture.open(0); //0 for built in webcam, 1 for external

    if (!capture.isOpened())
    {
        cout << "Cannot open video device or file!" << endl;
        return -1;
    }

    while(true){
Mat frame, gray_frame, grayThresh;


namedWindow("gray video", CV_WINDOW_AUTOSIZE);

//capture footage
capture >> frame;
if(frame.empty())
break;

//convert to 8 bit grayscale
cvtColor(frame, gray_frame, CV_BGR2GRAY);

//call the thresholding function
grayThresh = thresholdIMG(gray_frame, 170, 255);

imshow("gray video", grayThresh);

//hit q to end program
if ((char)waitKey(1) == 'q')
break;


}

}
```

without extracting coordinates, but just trying to show the thresholded image, it give me; "segmentation fault (core dumped)"

can anyone tell me what im misunderstanding here?

the thresholding function sort of works, if the return part is in the for-x loop, in which case it can thresh hold something like 4/5 of the top line. 

i really am out of ideas, any help will be happily welcomed :)

---

### Post by spjackson on 2012-11-26
> **rasmus91 said:**
> 
without extracting coordinates, but just trying to show the thresholded image, it give me; "segmentation fault (core dumped)"

can anyone tell me what im misunderstanding here?

the thresholding function sort of works, if the return part is in the for-x loop, in which case it can thresh hold something like 4/5 of the top line. 

For each of your 3 for loops that use <=, consider whether this is correct or whether < should be used instead.

---

### Post by rasmus91 on 2012-11-26
Did this.

had some help from a student whos been here longer than me, it works now. thanks for your time :)

---

