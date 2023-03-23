# Here are my random notes
### Batch resize images jpg from powershell using image magick

run ps script from your folder

```
foreach($f in $files) {
 $outfile= $f.DirectoryName+"\"+$f.BaseName+"R"+$f.Extension
 magick convert $f.FullName -resize 30%% $outfile
}
```

### Convert PDF to JPEG

https://jdhao.github.io/2019/11/20/convert_pdf_to_image_imagemagick/

Using Image Magick `magick  -density 150 presentation.pdf -quality 90 output-%3d.jpg`

The generated images will be named output-001.jpg, output-002.jpg

To convert a single page of PDF to image, use the following command:
```
convert -density 150 presentation.pdf[0] -quality 90 test.jpg
```
The number inside the bracket is used to select a page. Note that the page index starts at 0 instead of 1.

To resize the converted image, you can supply the -resize option:
```
convert -density 150 presentation.pdf[0] -quality 90 -resize 50% test.jpg
```
### How to compress jpg and generate pdf from set of images (we get very small pdf, may be less than 2Mb per 10 pages with those settings)

Here are two commands :
```
magick convert %1.JPG -sampling-factor 4:2:0 -strip -quality 55 -interlace Plane -gaussian-blur 0.05 -colorspace RGB -resize 56%% %1Optimized.jpg
magick convert *Optimized.jpg %1.pdf
```

### How to check print server logs

Step 1: Enable Logging. 

In Event Viewer dashboard, click Applications and Services Logs --> Microsoft --> Windows --> Print Service --> Operational. Right click Operational, select properties. Check the Enable logging box. Click Apply and Ok. Print reports logging is now enabled.

Step 2: View it in Event Viewer.

In Event Viewer dashboard, click Applications and Services Logs --> Microsoft --> Windows --> Print Service --> Operational. Double click Operational. All print events can be viewed here.
