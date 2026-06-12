---
title: "[Hepl] Unterminated Quoted  String"
date: 2012-10-20
forum: Programming Talk
---

### Post by khanhklhn2 on 2012-10-20
```
menu_choice=""
current_cd=""
title_file="title.csv"
tracks_file="tracks.csv"
temp_file=/tmp/csv.$$

trap `rm -f $temp_file` EXIT



get_return(){
    echo -e "Press return \c"

    read x
    return 0


}
fet_confirm(){
    echo -e "Are rou sure? \c"
    while true
    do
        read x
        case "$x" in
            y | yes | Y | Yes | YES )
            return 0;;
            n | no | N | No | NO )
            echo
            echo "Cancelled"
            return 1;;
            *) echo "Please enter yes or no" ;;
        esac
    done
}

set_menu_choice() {
clear
    echo "Option :-"
    echo
    echo "    a) Add new CD"
    echo "    f) Find CD"
    echo "    c) Count the CDs anh tracks in the catalog"
    if [ "$cdcatnum" != "" ]; then
        echo "    l) List tracks on $cdtitle"
        echo "    r) Remove $cdtitle"
        echo "    u) Update tracks information for $cdtitle"
    fi
    echo "    q) Quit"
    echo
    echo -e "Please enter choice then press return \c"
    read meru_choice
return
}


insert_track() {
    echo $* >> $tracks_file
    return
}

insert_title() {
    echo $* >> $title_file
    return
}

add_record_tracks() {
    echo "Enter track information for this CD"
    echo "When no more tracks enter q"
    cdtrack=1
    cdttitle=""
    while [ "$cdttitle" != "q" ]
    do
        echo -e "Track $cdtrack, track title? \c"
        read tmp

    #        case "$tmp" in

    #        "")    continue
    #            ;;
    #        *,*)    echo "Sorry, no commas allowed"
    #            continue
    #            ;;
    #        esac
            cdttitle=${tmp%%,*}
            if [ "$tmp" != "cdttitle" ]; then
            echo "Sorry, no commas allowed"
            continue
            fi
        if [ -n "$cdttitle" ]; then
            if [ "cdttitle != "q" ]; then
            insert_track $cdcatnum,$cdtrack,$cdttitle
            fi
        else
            cdtrack=$((cdtrack-1))
        fi
    cdtrack=$((cdtrack+1))
    done
}


# This allows adding of a new CD
add_records() {
    # Prompt for the initial information
    echo -e  "Enter catalog number \c"
    read tmp
    cdcatnum=${tmp%%,*}

    echo -e "Enter title \c"
    read tmp
    cdtitle=${tmp%%,*}

    echo -e "Enter type \c"
    read tmp
    cdtype=${tmp%%,*}

    echo -e "Enter artist/composer \c"
    read tmp
    cdac=${tmp%%,*}

# Check that thay want to enter the onformation
    echo About to add new entry
    echo "$cdcatnum $cdtitle $cdtype $cdac"

if get_confirn ; then
    insert_title $cdcatnum,$cdtitle,$cdtype,$cdac
    add_record_tracks
else
    remove_records
fi


fint_cd() {
    if [ "$1" = "n" ]; then
        asklist=n
    else
        asklist=y
    fi
    cdcatnum=""
    echo -e "Enter a string to search for in the CD titles \c"
    read searchstr
    if [ "$searchstr" = "" ]; then
        return 0
    fi

    grep "$searchstr" $title_file > $temp_file
#    set $(wc -l $temp_file)
#    linesfound=$1
    linesfound=$(wc -l $temp_file)
    case "$linesfound" in
    0)    echo "Sorry, nothing found"
        get_return
        return 0
        ;;
    1)    ;;
    2)    echo "Sorry, not unique."
        echo "found the fillowing"
        cat $temp_file
        get_return
        return 0
    esac

IFS=","
read cdcatnum cdtitle cdtype cdac < $$temp_file
IFS=" "


if [ -z "$cdcatnum" ]; then
    echo "Sorry, cuold not extract catalog field from $temp_file"
    get_return
    return 0
fi 

echo

echo CAtalog number $cdcatnum
echo $$cdtitle
echo $cdtype
echo $cdac
echo
get_return

if [ "$asklist" = "y" ]; then
    echo -e "View tracks for this CD? \c"
    read x
    if [ "$x" = "y" ]; then
        echo
        list_tracks
        echo
    fi
fi
return 1
}
update_cd() {
if [ -z "$cdcatnum" ]; then
    echo "You must select a CD first"
    find_cd n
fi
if [ -n "$cdcatnum" ]; then
    echo "Current tracks are :-"
    list_tracks
    echo
    echo "This will re-enter the tracks for $cdtitle"
    get_confirm && {
        grep -v "^$cdcatnum" $tracks_file > $temp_file
        mv $temp_file $tracks_file
        cat $temp_file > $tracks_file
    echo
    add_record_tracks
    }
fi
return
}


# Buoc9

count_cds() {
    num_titles=$(wx -l $title_file)
    num_tracks=$(wc -l @tracks_file)
echo found $num_titles CDs, with a total of $num_tracks tracks
get_return
return
}

#  Buoc10

remove_record() {
    if [ -z "$cdcatnum" ]; then
        echo You must select a CD first
        find_cd n
    fi
    if [ -n "$cdcatnum" ]; then
        echo "You must about to delete $cdtitle"
        get_confirm && {
            grep -v "^$cdcatnum" $title_file > $temp_file
            mv $temp_file $title_file
            grep -v "^$cdcatnum" $tracks_file > $tamp_file
            mv $temp_file $tracks_file
            cdcatnum=""
            echo Entry removed
        }
        get_return
    fi
    return
}


# Buoc11:

list_tracks() {
if [ "$cdcatnum" = "" ]; then
    echo no CD selected yet
    return
else
    grep "$cdcatnum" $tracks_file > $temp_file
    set $(wc -l $temp_file)

num_tracks=$1
    if [ "$num_tracks" = "0" ]; then
    echo no tracks found for $cdtitle
    else {
        echo
        echo "$cdtitle :-"
        echo
        cut -f 2- -d , $temp_file
        echo }| more
    fi
fi
get_return
return
}

# Buoc12:

rm -f $temp_file
if [ ! -f $title_file ]; then
    touch $title_file
fi
if [ ! -f $tracks_file ]; then
    touch $tracks_file
fi

clear
echo
echo
echo "Mini CD manager"
sleep 3
quit=n
while [ "$quit" != "y" ];
do
    set_menu_choice
    case "$menu_choice" in
        a) add_recordd;;
        r) remove_records;;
        f) find_cd y;;
        u) update_cd;;
        c) count_cds;;
        l) list_tracks;;
        b)
        echo
        more $title_file
        echo
        get_return;;
    q | Q ) quit=y;;
    *) echo "Sorry, choice not recognized";;
    esac
done

rm -f $temp_file
echo "Finished"
exit 0

```

---

### Post by papibe on 2012-10-20
Hi khanhklhn2.

Could you tell us how can we help you?

Regards.

---

### Post by sisco311 on 2012-10-20
Welcome to the forums!

You didn't close the quote (") at the 92nd line. There are other syntax errors as well in your script, but I will let you try to correct them yourself. If you can't please feel free to ask for help.

---

### Post by khanhklhn2 on 2012-10-20
thanks

---

