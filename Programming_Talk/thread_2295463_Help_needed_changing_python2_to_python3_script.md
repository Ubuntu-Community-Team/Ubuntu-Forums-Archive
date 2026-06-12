---
title: "Help needed changing python2 to python3 script"
date: 2015-09-18
forum: Programming Talk
---

### Post by lance bermudez on 2015-09-18
The code was written in python2 using the strand library used 2to3 on script to change to python3 I'm getting the error.
```

$ python3 pfish.py --sha256 -d /tmp/Test/ -r /home/lance/Python_Forensic/logs/ -v
Command Line Processed: Successfully
Welcome to pfish ... version 1.0
Processing File: /tmp/Test/_pfish.py
========================================
Traceback (most recent call last):
  File "pfish.py", line 41, in <module>
    filesProcessed = _pfish.WalkPath()
  File "/home/lance/Python_Forensic/_pfish.py", line 86, in WalkPath
    result=HashFile(fname, file, oCVS)
  File "/home/lance/Python_Forensic/_pfish.py", line 173, in HashFile
    o_result.writeCSVRow(simpleName, theFile, fileSize, modifiedTime, accessTime, createdTime, hashValue, ownerID, groupID, mode)
  File "/home/lance/Python_Forensic/_pfish.py", line 266, in writeCSVRow
    self.writer.writerow((fileName, filePath, fileSize, mTime, aTime, cTime, hashVal, own, grp, mod))
TypeError: 'str' does not support the buffer interface

```

code for script pfish.py
```

#!/usr/bin/python3
# -*- coding: utf-8 -*-
# p-fish : Python File System Hash Program
# Author: C. Hosmer
# July 2013
# Version 1.0
#
'''
how to use
--sha256
Python pfish.py --hash -d dir -r report -v 
C:\p-fish > Python pfish.py --md5 -d “c:\\p-fish\\TESTDIR\\” -r “c:\\p-fish\\” –v
'''
import logging # Python Library logging functions
import time    # Python Library time manipulation functions
import sys     # Python Library system specific parameters
import _pfish  # _pfish Support Function Module

if __name__ =='__main__':
    PFISH_VERSION = '1.0'

    # Turn on Logging
    logging.basicConfig(filename='pFishLog.log', level=logging.DEBUG, format='%(asctime)s %(message)s')

    # Process the Command Line Arguments
    _pfish.ParseCommandLine()

    # Record the Starting Time
    startTime = time.time()

    # Record the Welcome Message
    logging.info('')
    logging.info('Welcome to pfish version '+PFISH_VERSION+' ... New Scan Started')
    logging.info('')
    _pfish.DisplayMessage('Welcome to pfish ... version ' +PFISH_VERSION)

    # Record some information regarding the system
    logging.info('System: '+sys.platform)
    logging.info('Version: '+sys.version)
    
    # Traverse the file system directories and hash the files
    filesProcessed = _pfish.WalkPath()

    # Record the end time and calculate the duration
    endTime = time.time()
    duration = endTime-startTime
    logging.info('Files Processed: '+ str(filesProcessed))
    logging.info('Elapsed Time: '+ str(duration)+'seconds')
    logging.info('')
    logging.info('Program Terminated Normally')
    logging.info('')

    _pfish.DisplayMessage("Program End")

```

code for _pyfish.py script
```

#!/usr/bin/python3
# pfish support functions, where all the work get done
#
# All import from Python Standard Library
import os       # - Miscellaneous operating system interfaces
import stat     # - Function for interpreting os results
import time     # - Time access and conversions Functions
import hashlib  # - Secure hashes and message digests
import argparse # - Parser for commandline options, arguments
import csv      # - Reader & Writer for csv files
import logging  # - logging facility

log = logging.getLogger('main._pish')

#
#   Name: ParseCommand() Function
#   Desc: Process and Validate the line arguments
#         Use Python Standard Library module argparse
#
#  Input: None
#
# Action: Uses the standard Library argparse to process the command line
#         Establishes a global Variable gl_args where any of the functions can
#         Obtain argument information
#
def ParseCommandLine():
    parser = argparse.ArgumentParser('Python file system hashing...p-fish')
    parser.add_argument('-v', '--verbose', help='allows progress messages to be displayed', action='store_true')

    # setup a group where the selection is mutually exclusive and required.
    group = parser.add_mutually_exclusive_group(required=True)
    group.add_argument('--md5', help='specifies MD5 algorithm', action='store_true')
    group.add_argument('--sha256', help='specifies SHA256 algorithm', action='store_true')
    group.add_argument('--sha512', help='specifies SHA512 algorithm', action='store_true')
    parser.add_argument('-d', '--rootPath', type=ValidateDirectory, required=True, help="specify the root path for hashing")
    parser.add_argument('-r', '--reportPath', type=ValidateDirectoryWritable, required=True, help="specify the path for reports and logs will be written")

    # create a global object to hold the validated arguments,these will be available then
    # to all the Functions within the _pfish.py module
    
    global gl_args
    global gl_hashType

    gl_args=parser.parse_args()
    
    if gl_args.md5:
        gl_hashType='MD'
    elif gl_args.sha256:
        gl_hashType='SHA256'
    elif gl_args.sha512:
        gl_hashType='SHA512'
    else:
        gl_hashType="Unknown"
        logging.error('Unknown Hash Type Specified')
    DisplayMessage("Command Line Processed: Successfully")
    return

#
#   Name: WalkPath() Function
#   Desc: Walk the path specified on the command line
#         Use Python Standard Library module os and sys
#
#  Input: None, uses command line arguments
#
# Action: Uses the standard Library os and sys to 
#         Traverse the directory structure starting a root
#         Path specified by the user. For each file discovered, WalkPath
#         will call the Function Hashfile() to perform the file hashing
#         

def WalkPath():
    processCount=0
    errorCount=0
    oCVS=_CSVWriter(gl_args.reportPath+'fileSystemReport.csv', gl_hashType)

    # Create a loop that process all the files starting
    # at the rootPath, all sub-directories will also be
    # processed

    log.info('Root Path: '+gl_args.rootPath)

    for root, dirs, files in os.walk(gl_args.rootPath):
        # for each file obtain the filename and call the HashFile Function
        for file in files:
            fname=os.path.join(root, file)
            result=HashFile(fname, file, oCVS)
            
        # if hashing was successful then increment the ProcessCount
        if result is True:
            processCount += 1
            # if not successful, then increment the ErrorCount
        else:
            ErrorCount += 1
    oCVS.writerClose()
    return(processCount)

#
#   Name: HashFile() Function
#   Desc: Processes a single file which includes performing a hash of the file
#         Use Python Standard Library modules hashlib, os, and sys
#
#  Input: theFile=the full path of the file
#           simpleName=Just the filename itself
#
# Action: Attempts to hash the file and extract metadata 
#         Call GenerateReport for successful hashed files 
#         

def HashFile(theFile, simpleName, o_result):
    # Verify that the path is valid
    if os.path.exists(theFile):
        #Verify that the path is not a symbolic link
        if not os.path.islink(theFile):
            #Verify that the file is real
            if not os.path.islink(theFile):
                try:
                    #Attempt to open the file
                    f = open(theFile,'rb' )
                except IOError:
                    #if open fails report the error
                    log.warning( 'Open Failed:'+ theFile)
                    return
                else:
                    try:
                        # Attempt to read the file
                        rd = f.read()
                    except IOError:
                        # if read fails, then close the file and report error
                        f.close()
                        log.warning('Read Failed: '+theFile)
                        return
                    else:
                        # success the file is open and we can read from it
                        # lets query the file stats
                        theFileStats = os.stat(theFile)
                        (mode, ino, dev, nlink, uid, gid, size, atime, mtime, ctime) = os.stat(theFile)
                        #Print the simple file name
                        DisplayMessage("Processing File: " + theFile)
                        # print the size of the file in Bytes
                        fileSize = str(size)
                        #print MAC Times
                        modifiedTime = time.ctime(mtime)
                        accessTime = time.ctime(atime)
                        createdTime = time.ctime(ctime)
                        ownerID = str(uid)
                        groupID = str(gid)
                        fileMode = bin(mode)
                        #process the file hashes
                        if gl_args.md5:
                            #Calcuation and Print the MD5
                            hash = hashlib.md5()
                            hash.update(rd)
                            hexMD5 = hash.hexdigest()
                            hashValue = hexMD5.upper()
                        elif gl_args.sha256:
                            hash=hashlib.sha256()
                            hash.update(rd)
                            hexSHA256=hash.hexdigest()
                            hashValue=hexSHA256.upper()
                        elif gl_args.sha512:
                            #Calculate and Print the SHA512
                            hash=hashlib.sha512()
                            hash.update(rd)
                            hexSHA512=hash.hexdigest()
                            hashValue=hexSHA512.upper()
                        else:
                            log.error('Hash not Selected')
                    #File processing completed
                    #Close the Active File
                    print("========================================")
                    f.close()
                    # write one row to the output file
                    o_result.writeCSVRow(simpleName, theFile, fileSize, modifiedTime, accessTime, createdTime, hashValue, ownerID, groupID, mode)
                    return True
            else:
                log.warning('['+ repr(simpleName) +', Skipped NOT a File'+']')
                return False
        else:
            log.warning('['+ repr(simpleName) +', Skipped Link NOT a File'+']')
            return False
    else:
        log.warning('['+ repr(simpleName) +', Path does NOT exist'+']')
        return False

#
# Name: ValidateDirectory Function
#
# Desc: Function that will validate a directory path as
# existing and readable. Used for argument validation only
#
# Input: a directory path string
#
# Actions:
# if valid will return the Directory String
#
# if invalid it will raise an ArgumentTypeError within argparse
# which will in turn be reported by argparse to the user
#
def ValidateDirectory(theDir):
    # Validate the path is a directory
    if not os.path.isdir(theDir):
        raise argparse.ArgumentTypeError('Directory does not exist')
    # Validate the path is readable
    if os.access(theDir, os.R_OK):
        return theDir
    else:
        raise argparse.ArgumentTypeError('Directory is not readable')

#
# Name: ValidateDirectoryWritable Function
#
# Desc: Function that will validate a directory path as
#       existing and writable. Used for argument validation only
#
# Input: a directory path string
#
# Actions:
# if valid will return the Directory String
#
# if invalid it will raise an ArgumentTypeError within argparse
# which will in turn be reported by argparse to the user
#
def ValidateDirectoryWritable(theDir):
    # Validate the path is a directory
    if not os.path.isdir(theDir):
        raise argparse.ArgumentTypeError('Directory does not exist')
    # Validate the path is writable
    if os.access(theDir, os.W_OK):
        return theDir
    else:
        raise argparse.ArgumentTypeError('Directory is not writable')

# Name: DisplayMessage() Function
#
# Desc: Displays the message if the verbose command line option is present
#
# Input: message type string
#
# Actions:
# Uses the standard library print function to display the message
#
def DisplayMessage(msg):
    if gl_args.verbose:
        print(msg)
    return

#
# Class: _CSVWriter
#
# Desc: Handles all methods related to comma separated value operations
#
#Methods constructor: Initializes the CSV File
#  writeCVSRow: Writes a single row to the csv file
#  writerClose: Closes the CSV File
#
class _CSVWriter:
    def __init__(self, fileName, hashType):
        try:
            # create a writer object and then write the header row
            self.csvFile = open(fileName,'wb' )
            self.writer = csv.writer(self.csvFile, delimiter=',', quoting=csv.QUOTE_ALL)
            self.writer.writerow(('File', 'Path', 'Size', 'Modified Time', 'Access Time', 'Created Time', hashType, 'Owner', 'Group', 'Mode'))
        except:
            log.error('CSV File Failure')
    def writeCSVRow(self, fileName, filePath, fileSize, mTime, aTime, cTime, hashVal, own, grp, mod):
        self.writer.writerow((fileName, filePath, fileSize, mTime, aTime, cTime, hashVal, own, grp, mod))
    def writerClose(self):
        self.csvFile.close()

```

---

