# Questions

## What's `stdint.h`?

*stdint.h* allows programmers to write more portable code by providing a set of typedefs that specify exact-width integer types,
together with the defined minimum and maximum allowable values for each type, using macros.


## What's the point of using `uint8_t`, `uint32_t`, `int32_t`, and `uint16_t` in a program?

1. *uint8_t* : unsigned integer, 8 bits, between 0 - 255
2. *uint32_t* : unsigned integer, 32 bits, between 0 - 4,294,967,295
3. *int32_t* : signed integer, 32 bits, between −2,147,483,648 - 2,147,483,648
4. *uint16_t* : unsigned integer, 16 bits, between 0 - 65,535

## How many bytes is a `BYTE`, a `DWORD`, a `LONG`, and a `WORD`, respectively?

1. *BYTE* : 1 Byte
2. *DWORD* : 4 Bytes
3. *LONG* : 4 Bytes
4. *WORD* : 2 Bytes

## How to BMP
Recall that a file is just a sequence of bits, arranged in some fashion. A 24-bit BMP file, then, is essentially just a sequence of
bits, (almost) every 24 of which happen to represent some pixel’s color. But a BMP file also contains some "metadata," information
like an image’s height and width. That metadata is stored at the beginning of the file in the form of two data structures generally
referred to as "headers," not to be confused with C’s header files. (Incidentally, these headers have evolved over time. This
problem only expects that you support the latest version of Microsoft’s BMP format, 4.0, which debuted with Windows 95.) The first
of these headers, called BITMAPFILEHEADER, is 14 bytes long. (Recall that 1 byte equals 8 bits.) The second of these headers, called
BITMAPINFOHEADER, is 40 bytes long. Immediately following these headers is the actual bitmap: an array of bytes, triples of which
represent a pixel’s color. (In 1-, 4-, and 16-bit BMPs, but not 24- or 32-, there’s an additional header right after
BITMAPINFOHEADER called RGBQUAD, an array that defines "intensity values" for each of the colors in a device’s palette.) However,
BMP stores these triples backwards (i.e., as BGR), with 8 bits for blue, followed by 8 bits for green, followed by 8 bits for red.
(Some BMPs also store the entire bitmap backwards, with an image’s top row at the end of the BMP file. But we’ve stored this problem
set’s BMPs as described herein, with each bitmap’s top row first and bottom row last.) In other words, were we to convert the 1-bit
smiley above to a 24-bit smiley, substituting red for black, a 24-bit BMP would store this bitmap as follows, where 0000ff signifies
red and ffffff signifies white; we’ve highlighted in red all instances of 0000ff.