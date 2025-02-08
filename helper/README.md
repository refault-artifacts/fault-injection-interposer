## Helper Scripts
The helper scripts are taken from 
[Microsoft/mfit](https://github.com/microsoft/mfit). They are used to take 
the DDR5 UDIMM pinout from a text file (DIMM-DDR5-288pins.txt) that was 
copied manually from the [Micron DDR5 UDIMM Core datasheet](https://media-www.micron.com/-/media/client/global/documents/products/data-sheet/modules/unbuffered_dimm/ddr5/ddr5_udimm_core.pdf?rev=fdbd9476506c4e019360a5e402827caa).
They allow for easy double-checking of the pinout and, most importantly,
automation of the process of creating schematic symbols in KiCad.

It is to note that the scripts generate the files in a legacy format that 
is not standard anymore with new versions of KiCad (Version 6). It is a 
simpler line-based format, where the new version uses a lisp-style 
s-expression format. Also the stdout output of the script is not usable 
directly as a KiCad file, instead the 
following had to be added to the *.lib file:
```
EESchema-LIBRARY Version 2.3 Date: 2023-02-20
#encoding utf-8
# start
DEF DDR5 U 0 10 Y Y 1 L N
DRAW

...

ENDDRAW
ENDDEF
# to 288 done
```
to make the import work.
The documentation of the legacy format can be found [here.](https://dev-docs.kicad.org/en/file-formats/legacy-4-to-6/legacy_file_format_documentation.pdf)

At some point it might be a good idea to rewrite the scripts so they generate
proper files (in s-expression format).


