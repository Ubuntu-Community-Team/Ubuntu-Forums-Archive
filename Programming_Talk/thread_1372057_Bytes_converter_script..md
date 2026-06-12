---
title: "Bytes converter script."
date: 2010-01-04
forum: Programming Talk
---

### Post by ProgramErgoSum on 2010-01-04
Hi,
I wrote this script to test my shell scripting skills. This script converts bytes to KB, MB, GB and TB or back to lower units. The base factor is 1024 which is raised to an exponent based on the target size.

Can someone tell me how I can plus this into the ls -l command so that I can see file listing in KB, MB, etc. ?

```

#USAGE bconv n b|KB|MB|GB|TB b|KB|MB|GB|TB

usage_text () {
    echo "USAGE : bconv n from_size to_size"
    echo "      from_size : b|KB|MB|GB|TB "
    echo "      to_size   : b|KB|MB|GB|TB "
    echo "      bconv -h"
}

help_text () {
    echo "bconv : A quick calculator to see bytes in different units"
    echo "USAGE : bconv n b|KB|MB|GB|TB b|KB|MB|GB|TB "
    echo "Example : bconv 93470746 b MB"
    echo "Result : 93470746 b = 89.1406 MB"
}

check_args () {
    #Filesize should be numeric

    if ! [[ $FILE_SIZE =~ [[:digit:]] ]] ; then
        echo "$FILE_SIZE File size argument is not numeric"
        usage_text 
        exit 8
    fi

    #From filesize should be one of the size units
    if ! [[ $FROM_SIZE =~ [b]|[KB]|[MB]|[GB]|[TB] ]] ; then
        echo "$FROM_SIZE From file size argument is one of the size units"
        usage_text
        exit 8
    fi

    #To filesize should be one of the size units
    if ! [[ $TO_SIZE =~ [b]|[KB]|[MB]|[GB]|[TB] ]] ; then
        echo "$TO_SIZE To file size argument is one of the size units"
        usage_text
        exit 8
    fi

    #From and to size units should be different
    if [ $FROM_SIZE = $TO_SIZE ] ; then
        echo "No conversion done ! FROM and TO filesize units are same."
        echo "${FILE_SIZE} ${FROM_SIZE} = ${FILE_SIZE} ${TO_SIZE}"
        exit 4
    fi

}

do_conversion () {
    from_size=( "" "b" "KB" "MB" "GB" "TB" )
    to_size=( "" "b" "KB" "MB" "GB" "TB" )
    base_factor=1024

    case ${FROM_SIZE} in 
            "b") from_unit=1  ;;
            "KB") from_unit=2 ;;
            "MB") from_unit=3 ;;
            "GB") from_unit=4 ;;
            "TB") from_unit=5 ;;
    esac

    case ${TO_SIZE} in 
            "b") to_unit=1  ;;
            "KB") to_unit=2 ;;
            "MB") to_unit=3 ;;
            "GB") to_unit=4 ;;
            "TB") to_unit=5 ;;
    esac
    
    if [ ${from_unit} -lt ${to_unit} ] ; then
        let "expo=$to_unit-$from_unit"
        new_size=$( echo "scale=4; ${FILE_SIZE}/${base_factor}^${expo}" | bc)
    else
        let "expo=$from_unit-$to_unit"
        new_size=$( echo "scale=2; ${FILE_SIZE}*${base_factor}^${expo}" | bc)
    fi
}


# Check arguments. 
case $# in
        3) FILE_SIZE="$1" 
           FROM_SIZE="$2"
           TO_SIZE="$3" 
           check_args ${FILE_SIZE} ${FROM_SIZE} ${TO_SIZE} 
           do_conversion ${FILE_SIZE} ${FROM_SIZE} ${TO_SIZE}
           echo "${FILE_SIZE} ${FROM_SIZE} = ${new_size} ${TO_SIZE}"
           exit 0
           ;;
        1) getopts "h" option
           help_text ${one_arg}
           exit 4
           ;;
        *) usage_text 
           exit 4
           ;;
esac 

```

---

