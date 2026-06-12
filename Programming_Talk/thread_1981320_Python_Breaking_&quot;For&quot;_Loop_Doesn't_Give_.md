---
title: "Python: Breaking &quot;For&quot; Loop Doesn't Give Desired Results"
date: 2012-05-16
forum: Programming Talk
---

### Post by dodle on 2012-05-16
I've created a python script that takes corrupted jpeg images and removes garbage from the beginning of the file. I use a [color=red]for[/color] loop to iterate through the file and find the JFIF header. Sometimes the images contain more than one JFIF header so I have to [color=red]break[/color] out of the loop after the first header is found. But for some reason the [color=red]break[/color] causes the program to report that the image is not corrupted. I haven't been able to figure out what my problem is yet.

Here is the portion of the code giving me the problem:
[php]...
...
# JFIF header
jfif = (('ff', 'd8', 'ff', 'e0', '00', '10'), ('4a', '46', '49', '46'))
...
...
jpeg = open(image, 'rb')

jpeg_data = jpeg.read()
jpeg_data = array.array('B', jpeg_data)

jpeg.close()

def ToHex(b):
    return '%02x' % b

def HexToInt(h):
    return int(h, 16)

try:
    # If JFIF header is not found, image is reported as not fixable
    corrupt = 2
    for byte in xrange(len(jpeg_data)):
        if ToHex(jpeg_data[byte]) == jfif[1][0]:
            if ToHex(jpeg_data[byte+1]) == jfif[1][1]:
                if ToHex(jpeg_data[byte+2]) == jfif[1][2]:
                    if ToHex(jpeg_data[byte+3]) == jfif[1][3]:
                        # JFIF header found
                        corrupt = 0
                        garbage = list(jpeg_data[:byte])
                        for g in xrange(len(garbage)):
                            garbage[g] = ToHex(garbage[g])
                        if garbage != list(jfif[0]):
                            # If JFIF header is found with garbage before, it is reported as fixable
                            corrupt = 1
                        new_jpeg_data = array.array('B', jpeg_data[byte:])
                        prefix_bytes = len(jfif[0])
                        for p in xrange(prefix_bytes):
                            prefix_bytes -= 1
                            new_jpeg_data.insert(0, HexToInt(jfif[0][prefix_bytes]))
                        # Ensure that iteration ends after first JFIF header
                        break
    if corrupt:
        if corrupt == 2:
            print('\nERROR: Could not repair %s!\n' % image)
            logger.error('Could not repair %s!' % image)
        else:
            name = '.'.join(os.path.basename(image).split('.')[:-1])
            name = '%s_fix.jpg' % name
            print('Fixing %s and saving to %s' % (image, name))
            logger.info('Fixing %s and saving to %s' % (image, name))
            new_jpeg = open(name, 'wb')
            new_jpeg.write(new_jpeg_data)
            new_jpeg.close()
    else:
        print('\nWARNING: %s does not appear to be corrupt, skipping!\n' % image)
        logger.warning('%s does not appear to be corrupt, skipping!' % image)
        #time.sleep(4)
except IndexError:
    print('\ERROR: Could not repair %s!\n' % image)
    logger.error('Could not repair %s!' % image)[/php]

I created a test script to see if I could find the error, but the test results the way I want it.
[php]#! /usr/bin/env python

jfif = (('ff', 'd8', 'ff', 'e0', '00', '10'), ('4a', '46', '49', '46'))

# Pseudo jpeg data with garbage before JFIF header
jpeg_data = ('aa', 'a0', '4a', '46', '49', '46', 'b9', '7d', '4a', '46', '49', '46')

def HexToInt(h):
    return int(h, 16)

# If JFIF header is not found, image is reported as not fixable
corrupt = 2
for byte in xrange(len(jpeg_data)):
    if jpeg_data[byte] == jfif[1][0]:
        print('4a')
        if jpeg_data[byte+1] == jfif[1][1]:
            print('46')
            if jpeg_data[byte+2] == jfif[1][2]:
                print('49')
                if jpeg_data[byte+3] == jfif[1][3]:
                    print('46')
                    corrupt = 0
                    garbage = list(jpeg_data[:byte])
                    for g in xrange(len(garbage)):
                        garbage[g] = garbage[g]
                    if garbage != list(jfif[0]):
                        # If JFIF header is found with garbage before, it is reported as fixable
                        corrupt = 1
                    new_jpeg_data = list(jpeg_data[byte:])
                    prefix_bytes = len(jfif[0])
                    for p in xrange(prefix_bytes):
                        prefix_bytes -= 1
                        new_jpeg_data.insert(0, jfif[0][prefix_bytes])
                    # Ensure that iteration ends after first JFIF header
                    break

if corrupt:
    if corrupt == 2:
        print('\nERROR: Could not repair image!\n')
    else:
        print('Fixing image and saving')
        print(new_jpeg_data)
else:
    print('\nWARNING: image does not appear to be corrupt, skipping!\n')[/php]


**----- EDIT -----**

I think the problem is in this area of code:
[php]if garbage != list(jfif[0]):
    # If JFIF header is found with garbage before, it is reported as fixable
    corrupt = 1[/php]


**----- SOLVED -----**

Okay, my mistake. It seems to be working fine. The jpeg image I was testing with wasn't what I thought.

---

