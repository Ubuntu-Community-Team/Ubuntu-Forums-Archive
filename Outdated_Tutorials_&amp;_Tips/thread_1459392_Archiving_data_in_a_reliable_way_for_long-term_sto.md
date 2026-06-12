---
title: "Archiving data in a reliable way for long-term storage"
date: 2010-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Sporkman on 2010-04-21
As we all know, important data needs to be backed up on a regular basis. Some data are better suited for long-term storage - these would be files that don't need to be regularly updated, but which you want to preserve and read on occasion, such as financial records, photos, videos, music, past work, etc.

Unfortunately, physical media can degrade over time, and the data stored on them can become corrupted. To improve the odds that the data on a particular medium will be fully recoverable over a long period of time, I propose archiving the data in a way that includes data verification and redundancy.

Below is a script that will archive data in a manner that includes verification via a sha512sum hash, and redundancy via the par2 data recovery tool, which uses the Reed-Solomon method of data recovery.

The cost is the extra storage capacity necessary for the redundancy and verification data (set in the script at 20%), as well as the extra complexity of the archive process itself.

```
#!/bin/bash

#
# Data archiving tool, with verification and data redundancy
#
# Sporkman, 4/20/10
#
# For a given source file or directory, creates an archive directory holding the
# tar'd source as well as verification info. Specifically, the contents of the
# archive directory are:
#
# 1. The tar'd source, split into chunks,
# 2. A copy of this script (as it was when the archive was created),
# 3. A sha512sum hash check file,
# 4. A series of data files (*.par2) used by par2 to verify and repair the data
#       tar file chunks.
#
# The purpose of this utility is to enable long-term storage of data on media
# which may become corrupted over time.
#

DATA_FNAME="data.tar"
HASH_FNAME="hash"

DATA_REDUNDANCY_PCT="20"
SPLIT_FILE_SIZE="100M"

infomsg ()
{
   echo ""
   echo "$1"
}

errmsg ()
{
   infomsg "$1"
   echo ""
   exit 1
}

checkres ()
{
   if [ $1 -ne 0 ]; then
      errmsg "Failed."
   fi
}

print_usage()
{
   echo ""
   echo "Usage:"
   echo ""
   echo "   To create an archive:"
   echo ""
   echo "      archive c <source path> <dest dir> <dest name>"
   echo ""
   echo "   To extract an archive:"
   echo ""
   echo "      archive x <archive path> <dest dir>"
   echo ""
   echo "   To check (\"verify\") an archive:"
   echo ""
   echo "      archive v <archive path>"
   echo ""
   echo ""
   exit 1
}

check_archive ()
{
   # Remove any trailing slashes
   ARC="${1/%\//}"

   if [ ! -e "$ARC" ]; then
      errmsg "Error: Archive doesn't exist"
   fi
   
   if [ ! -d "$ARC" ]; then
      errmsg "Error: Archive is not a directory as it should be"
   fi
   
   infomsg "Checking archive integrity..."
   
   RETVAL=0
   
   if [ ! -e "${ARC}/${DATA_FNAME}.aaaa" ]; then
      infomsg "Error: Data file is missing"
      RETVAL=1
   fi
   
   if [ ! -e "${ARC}/${HASH_FNAME}" ]; then
      infomsg "Error: Hash file is missing"
      RETVAL=1
   fi
   
   if [ ! -e "${ARC}/${DATA_FNAME}.aaaa.par2" ]; then
      infomsg "Error: par2 verification file is missing"
      RETVAL=1
   fi
   
   if [ $RETVAL -ne 0 ]; then
      return $RETVAL
   fi

   MYPWD=`pwd`

   cd ${ARC}

   sha512sum --status -c ${HASH_FNAME}
   
   if [ $? -ne 0 ]; then
      infomsg "Error: hash verification failed"
      RETVAL=2
   fi

   cd $MYPWD
   
   if [ $RETVAL -ne 0 ]; then

      par2 v -qq ${ARC}/${DATA_FNAME}.*
   
      if [ $? -ne 0 ]; then
         infomsg "Error: par2 verification failed"
      fi
   fi
   
   return $RETVAL
}

create_archive ()
{
   # Remove any trailing slashes
   SRC="${2/%\//}"
   DST="${3/%\//}"
   NM="${4/%\//}"

   SRCDIR=`dirname ${SRC}`
   SRCNM=`basename ${SRC}`

   if [ ! -e "$SRC" ]; then
      errmsg "Error: Source path doesn't exist"
   fi
   
   if [ ! -e "$DST" ]; then
      errmsg "Error: Destination directory doesn't exist"
   fi
   
   if [ ! -d "$DST" ]; then
      errmsg "Error: Destination directory is not a directory"
   fi
   
   if [ -e "${DST}/${NM}" ]; then
      errmsg "Error: Destination name already exists"
   fi
   
   infomsg "Creating archive directory..."
   
   mkdir ${DST}/${NM}
   
   checkres $?
   
   cp ${0} ${DST}/${NM}
   
   checkres $?
   
   infomsg "Archiving source data..."
   
   MYPWD=`pwd`
   
   cd "${SRCDIR}"
   checkres $?
   
   ARCDIR="${DST}/${NM}"

   if [ "${DST:0:1}" != "/" ]; then
      ARCDIR="${MYPWD}/${ARCDIR}"
   fi

   FNAME="${ARCDIR}/${DATA_FNAME}"
   
   tar --totals -cv ${SRCNM} | split --bytes=${SPLIT_FILE_SIZE} --suffix-length=4 - ${FNAME}.
   
   checkres $?
   
   cd "${ARCDIR}"
   checkres $?
   
   infomsg "Calculating hash..."
   
   for f in `ls -1 ${DATA_FNAME}.*`; do
      sha512sum -b ${f} >> ${HASH_FNAME}
   done
   
   checkres $?
   
   cd "${MYPWD}"
   checkres $?
   
   infomsg "Generating redundancy data..."
   
   for f in `ls -1 ${FNAME}.*`; do
      par2 c -qq -r${DATA_REDUNDANCY_PCT} ${f}
   done
   
   checkres $?
   
   check_archive "${ARCDIR}"
   
   checkres $?
}

extract_archive ()
{
   # Remove any trailing slashes
   ARC="${2/%\//}"
   DST="${3/%\//}"
   
   if [ ! -e "$DST" ]; then
      errmsg "Error: Destination directory doesn't exist"
   fi
   
   if [ ! -d "$DST" ]; then
      errmsg "Error: Destination directory is not a directory"
   fi
   
   check_archive "$ARC"
   
   RES=$?
   
   if [ $RES -eq 1 ]; then
   
      errmsg "Error: Archive is incomplete. Extraction will need to be done manually."
      
   elif [ $RES -eq 2 ]; then
   
      infomsg "Warning: Archive appears to be corrupted. Will attempt to repair..."
      
      MSG=0
      
      for f in `ls -1 ${ARC}/${DATA_FNAME}.*`; do
         par2 r "${f}.par2"
      
         if [ $? -ne 0 ]; then
            if [ $MSG -eq 0 ]; then
               infomsg "Archive repair was unsuccessful. Will attempt to extract anyways."
               MSG=1
            fi
         fi
      done
          
   else
      infomsg "Archive looks ok."
   fi
   
   infomsg "Extracting archive to ${DST} ..."
   
   infomsg "(Output suppressed - see ${DST}/archive_x_log for details)"
   
   MYPWD=`pwd`
   
   cd ${DST}
   checkres $?
   
   TARFILE="${ARC}/${DATA_FNAME}"

   if [ "${ARC:0:1}" != "/" ]; then
      TARFILE="${MYPWD}/${TARFILE}"
   fi

   cat ${TARFILE}.???? | tar -xv  > archive_x_log 2>&1
   
   checkres $?
   
   cd "${MYPWD}"
   checkres $?
}


#
#
#
#

if [ "`which tar`" == "" ]; then
   errmsg "Error: tar needs installed"
fi

if [ "`which par2`" == "" ]; then
   errmsg "Error: par2 needs installed"
fi

if [ "`which sha512sum`" == "" ]; then
   errmsg "Error: sha512sum needs installed"
fi

MODE="${1}"

if [ "$MODE" == "c" ]; then

   if [ $# -ne "4" ]; then
      print_usage
   fi
   
   create_archive "$@"
   
elif [ "$MODE" == "x" ]; then

   if [ $# -ne "3" ]; then
      print_usage
   fi
   
   extract_archive "$@"
   
elif [ "$MODE" == "v" ]; then

   if [ $# -ne "2" ]; then
      print_usage
   fi
   
   shift
   check_archive "$@"
   
   RES=$?
   
   if [ $RES -eq 1 ]; then
   
      errmsg "Error: Archive is incomplete. Extraction would need to be done manually."
      
   elif [ $RES -eq 2 ]; then
   
      infomsg "Warning: Archive appears to be corrupted."
            
   else
      infomsg "Archive looks ok."
   fi

else

   print_usage
   
fi

infomsg "Done."
echo ""
exit 0

```


**04-29-2001 Edit:** Modified to separate tar file into manageable chunks, fixed check_archive() to return status code, removed --verify flag from tar archive create as it seems problematic.

---

