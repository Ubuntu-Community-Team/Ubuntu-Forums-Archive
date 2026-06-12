---
title: "Change script to delete rar files after sucessful unpack"
date: 2013-02-03
forum: Programming Talk
---

### Post by felipesalomao on 2013-02-03
Hi guys, i use script (.sh) that automatically unpack rar and zip files, i would like to modify it to delete all rar files (rar, r01, r02, etc) after sucessful unpack.

See script:

```
#!/bin/sh

set -x

TR_DIR="${TR_TORRENT_DIR}"
TR_NAME="${TR_TORRENT_NAME}"

QPKG_DIR=`/sbin/getcfg Transmission Install_Path -f /etc/config/qpkg.conf`
FIND_PATH="${QPKG_DIR}/bin/find"
LOG_FILE_PATH="${QPKG_DIR}/web-gui/admin/logs/unpack.log"   #PATH to store the log file, blank to disable
UNRAR_TRIGGERS="x -y -o+ -idp" #triggers for unrar operation, use this to control the info logged (see unrar command manual)
UNZIP_TRIGGERS="-o" #same as unrar but for zip.
DECOMPRESS_TO_DIR=`/sbin/getcfg unzip_unrar DECOMPRESS_TO -f ${QPKG_DIR}/conf/addons.conf` #If blank will unpack in its own directory, else will unpack to a fixed directory
ACTION_TIME=$(date +%d-%m-%Y\ %H:%M:%S)

if [ -z $DECOMPRESS_TO_DIR ]; then
	DESTINATION_DIR="$TR_DIR"
else
	DESTINATION_DIR="$DECOMPRESS_TO_DIR/"
fi

	cd "$TR_DIR"
	if [ -d "$TR_NAME" ]; then
		cd "$TR_NAME"	
		IFS=$'\n'
		unset RAR_FILES i
		FIND_RESULTS=`$FIND_PATH -maxdepth 2 -iname "*.rar"`
		for RAR_FILE in $FIND_RESULTS; do
			if [[ $RAR_FILE =~ .*part.*.rar ]]; then
				if [[ $RAR_FILE =~ .*part0*1.rar ]]; then
					RAR_FILES[i++]=$RAR_FILE
				fi
			else
				RAR_FILES[i++]=$RAR_FILE; -delete
			fi
              
		done
		unset IFS
		unset FIND_RESULTS
		

		if [ ${#RAR_FILES} -gt 0 ]; then
		mkdir -p "$DESTINATION_DIR"
		for RAR_FILE in "${RAR_FILES[@]}"; do
			/opt/bin/unrar $UNRAR_TRIGGERS "$RAR_FILE" "$DESTINATION_DIR/$TR_NAME" >> $LOG_FILE_PATH
			if [ $? -gt 0 ]; then
				echo $ACTION_TIME "Error unrarring $TR_NAME torrent" >> $LOG_FILE_PATH
				exit 0
			else
				echo $ACTION_TIME "Unrarred $TR_NAME torrent" >> $LOG_FILE_PATH
			fi
		done
        fi
		
		IFS=$'\n'
		FIND_RESULTS=`$FIND_PATH -maxdepth 2 -iname "*.zip"`
		for ZIP_FILE in $FIND_RESULTS; do
			ZIP_FILES[i++]=$ZIP_FILE
		done
		if [ ${#ZIP_FILES} -gt 0 ]; then
			mkdir -p "$DESTINATION_DIR"
			for ZIP_FILE in "${ZIP_FILES[@]}"; do
				/opt/bin/unzip $UNZIP_TRIGGERS "$ZIP_FILE" -d "$DESTINATION_DIR/$TR_NAME" >> $LOG_FILE_PATH
				if [ $? -gt 0 ]; then
					echo $ACTION_TIME "Error unziping $TR_NAME torrent" >> $LOG_FILE_PATH
					exit 0
				else
					echo $ACTION_TIME "Unziped $TR_NAME torrent" >> $LOG_FILE_PATH
				fi
			done
		fi
		unset IFS
		
	#in case the torrent is a file	
	else
		#special case when the torrent name contains the archive extension
		FILENAME=`${QPKG_DIR}/bin/basename "$TR_NAME" .rar`

		if [ -f "$FILENAME.rar" ]; then
			echo "Special rar archive found ..."
			
			if [ -z "$DECOMPRESS_TO_DIR" ]; then
				DESTINATION_DIR="${TR_DIR}/$FILENAME"
			else
				DESTINATION_DIR="$DECOMPRESS_TO_DIR/$FILENAME"
			fi
			
			mkdir -p "$DESTINATION_DIR"
			
			/opt/bin/unrar $UNRAR_TRIGGERS "$FILENAME.rar" "$DESTINATION_DIR" >> $LOG_FILE_PATH
			if [ $? -gt 0 ]; then
				echo $ACTION_TIME "Error unrarring $TR_NAME torrent" >> $LOG_FILE_PATH
				exit 0
			else
				echo $ACTION_TIME "Unrarred $TR_NAME torrent" >> $LOG_FILE_PATH
			fi
		else	
			if [ -f "$TR_NAME.rar" ]; then
				mkdir -p "$DESTINATION_DIR"
				/opt/bin/unrar $UNRAR_TRIGGERS "$TR_NAME.rar" "$DESTINATION_DIR" >> $LOG_FILE_PATH
				if [ $? -gt 0 ]; then
					echo $ACTION_TIME "Error unrarring $TR_NAME torrent" >> $LOG_FILE_PATH
					exit 0
				else
					echo $ACTION_TIME "Unrarred $TR_NAME torrent" >> $LOG_FILE_PATH
				fi
			fi
		fi

		FILENAME=`${QPKG_DIR}/bin/basename "$TR_NAME" .zip`

		if [ -f "$FILENAME.zip" ]; then
			echo "Special zip archive found ..."
			mkdir -p "$DESTINATION_DIR"
			/opt/bin/unzip $UNZIP_TRIGGERS "$FILENAME.zip" -d "$DESTINATION_DIR" \ >> $LOG_FILE_PATH
			if [ $? -gt 0 ]; then
				echo $ACTION_TIME "Error unzipping $TR_NAME torrent" >> $LOG_FILE_PATH
				exit 0
			else
				echo $ACTION_TIME "Unziped $TR_NAME torrent" >> $LOG_FILE_PATH
			fi
		else
			LIST_ZIP_FILE=`ls "$TR_NAME.zip" 2>/dev/null`
			if [ ! -z "$LIST_ZIP_FILE" ]; then
				mkdir -p "$DESTINATION_DIR"
				/opt/bin/unzip $UNZIP_TRIGGERS "$LIST_ZIP_FILE" -d "$DESTINATION_DIR" >> $LOG_FILE_PATH
				if [ $? -gt 0 ]; then
					echo $ACTION_TIME "Error unzipping $TR_NAME torrent" >> $LOG_FILE_PATH
					exit 0
				else
					echo $ACTION_TIME "Unziped $TR_NAME torrent" >> $LOG_FILE_PATH
				fi
			fi
		fi
	fi
```

---

### Post by ntzrmtthihu777 on 2013-02-04
Hmm, does not unrar and unzip have a list function? You can set it to detect the presence of the zipped files contents and delete if found, or just simply add a rm for each of your cases here, like rm $TR_NAME.rar, rm $FILE_NAME.rar, etc. Multipart rar files may be trickier to do, but I'm sure you can get it right.

---

