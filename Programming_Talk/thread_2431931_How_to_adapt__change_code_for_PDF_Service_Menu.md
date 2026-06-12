---
title: "How to adapt / change code for PDF Service Menu?"
date: 2019-11-24
forum: Programming Talk
---

### Post by Chip88 on 2019-11-24
Hi there,

I'm using the [KDE 5 Service Menu PDF]("https://store.kde.org/p/1227799/") and I'm very satisfied with it.
I already changed some parts of the code to my needs.

Because I have to convert often PDF files into PNG or JPG, I would like to aim the following:
If I have a **PDF with many pages**, the the name of the converted file should have - as originally intended - **a number**, so all pages are getting converted correctly:
```
-sOutputFile="${file_name%.*}_%0d.jpg"
```
and
```
-sOutputFile="${file_name%.*}_%0d.png"
```

But if I have a **PDF with a single page**, the the name of the converted file should have **no number**.


Benigno, who made the Service Menu, gave me the advice to insert a check before saving the files. With ***pdfinfo*** you can know the number of pages and if the pdf has only one page, then you save the file without numbering.


He told me the snippet that should be adapted is the following one:```
pages=$(pdfinfo file.pdf | grep Pages | sed "s/.*:\s*//")
if [ $pages -eq 1 ]; then
echo "Only one page"
else
echo "Many pages"
fi
```

Unfortunately, I'm not a big programmer and don't know exactly how to adapt this snippet and where to insert the mentioned check for the number of pages.


My code for converting PDF to PNG is looking like this:


```
png () {
encoding=$1
shift


[ -z "${dpi}" ] && dpi='300x300'


while [ $# -ne 0 ]; do
work_dir="${1%/*}"; [ ! -d "${work_dir}" ] && work_dir="$(pwd)"
file_name="${1##*/}"
base_file_name="${file_name%.*}"


## Reload language strings with current variables
load_language


eval output_dir=\$"msg_png_dest_dir_${encoding}"
if [ -d "${output_dir}" ]; then
output_dir=$(kdialog --title "${msg_png_select_output_dir_title}" --getexistingdirectory "${work_dir}") || exit 0
fi


[ ! -f "${work_dir}/${file_name}" ] && shift && "${kdialog_bin}" --title "${msg_finish_title}" --passivepopup "${msg_file_not_found}" 5 && continue
"${gs_bin}" -dSAFER -dBATCH -dNOPAUSE -q -dTextAlphaBits=4 -dGraphicsAlphaBits=4 -sDEVICE="${encoding}" -r"${dpi}" -sOutputFile="${file_name%.*}_%0d.png" "${1}" && \
        "${kdialog_bin}" || \
"${kdialog_bin}" --title "${msg_png_finish_title}" --passivepopup "${msg_png_finish_error}" 5
shift
done
}

```
Maybe someone has an idea, how to change that code aiming that depending on the number of the pages of the PDF there is a numbering or not.

Thank you in advance about your support & a timely response!

A somehow desperate
Chipy

---

### Post by norobro on 2019-11-24
The following is untested:```
pages=$(pdfinfo "$file_name" | grep Pages | sed "s/.*:\s*//")
if [ $pages -eq 1 ]; then
    output_filename="${file_name%.*}.png"
else
    output_filename="${file_name%.*}_%0d.png"
fi

# Then use the above variable in the ghostscript command
"${gs_bin}" ...  -sOutputFile="$output_filename" "${1}" ...
```

---

