[中文文档](<https://github.com/waynerv/github-markdown-toc/blob/master/README.md>) | [Readme](<https://github.com/waynerv/github-markdown-toc/blob/master/README_eng.md>)

## Table of Contents

  - [Table of Contents](#table-of-contents)
  - [md-toc](#md-toc)
  - [Installation](#installation)
  - [Usage](#usage)
    - [Single file](#single-file)
    - [Multiple files](#multiple-files)
    - [Configuration](#configuration)
      - [customize  the title level](#customize--the-title-level)
      - [Write results to a file or print to standard output](#write-results-to-a-file-or-print-to-standard-output)
  - [Dependency](#dependency)

## md-toc

Easy and customizable way to **generate TOC** for README.md on GitHub.

- Automatically generate table of contents in accordance with Github Favored Markdown format
- Just a single .py file can be done with no other dependencies
- Support for text content in both Chinese and English languages
- Support for customizing the title level of the table of contents
- Supports automatic write results to files, and also can print results to standard output for further processing
- Supports generating table of contents for multiple files at the same time
- Support for repeating headers, filtering headers in code blocks

If you don't want to download any files or read the command instructions below, you can try my online build tool.

## Installation

**Linux**

```
$ wget https://raw.githubusercontent.com/waynerv/github-markdown-toc/master/md-toc.py
```

You can also directly download the file `md-toc.py` in the root directory of the repository or copy the contents of the file to a local file with the same name.

**OSX or Windows**

Not tested yet.

## Usage

The command syntax is as follows：

```bash
$ python3 md-toc.py [-h] [-s {1,2,3,4,5,6}] [-e {1,2,3,4,5,6}] [-o] file [file ...]
```

Run the command as follows to get help information for the command options（you can replace `-h` with `--help`).:

```bash
$ python3 md-toc.py -h
```

Note: Make sure your device has successfully installed Python3 before run it.

### Single file

Automatically generate **TOC** for a single markdown file and print result to standard output with only 2-4 title levels:

```bash
$ python3 md-toc.py -s 2 -e 4 -o README_eng.md
Generate from file: README_eng.md

- [Table of Contents](#table-of-contents)
- [md-toc](#md-toc)
- [Installation](#installation)
- [Usage](#usage)
  - [Single file](#single-file)
  - [Multiple files](#multiple-files)
  - [Configuration](#configuration)
    - [customize  the title level](#customize--the-title-level)
    - [Write results to a file or print to standard output](#write-results-to-a-file-or-print-to-standard-output)
- [Dependency](#dependency)

Table of contents generated.
```

Then copy/paste result between prompt sentence from console into original README.md.

### Multiple files

Use the default configuration to generate **TOC** for multiple markdown files and write them to a file separately:

```bash
$ python3 md-toc.py file01.md file02.md file03.md
Table of contents generated.
```

here's an example：

- [File_without_TOC.md](https://github.com/waynerv/github-markdown-toc/blob/master/examples/File_without_TOC.md)

After generating **TOC** and writing to the file：

- [File_with_TOC.md](https://github.com/waynerv/github-markdown-toc/blob/master/examples/File_with_TOC.md)

### Configuration

#### customize  the title level

Use the command line options `-s` or `--start` and add parameters to set the start header level of **TOC**. The default value of the parameter is 1.

Use the command line options `-e` or `--end` and add parameters to set the end header level of **TOC**. The default value of the parameter is 6.

The title level parameter must be an integer between 1 and 6, and the start title level cannot be greater than the end title level.

```bash
-s {1,2,3,4,5,6}, --start {1,2,3,4,5,6}  choose the start level of TOC, default value is 1
-e {1,2,3,4,5,6}, --end {1,2,3,4,5,6}  choose the end level of TOC, default value is 6
```

Generate **TOC** of 1-6 title levels (default option):

```bash
$ python3 md-toc.py test/Mastering_Markdown.md -o
Generate from file: test/Mastering_Markdown.md

- [Mastering Markdown](#mastering-markdown)
  - [What is Markdown?](#what-is-markdown)
  - [Examples](#examples)
  - [Syntax guide](#syntax-guide)
    - [Headers](#headers)
    - [Emphasis](#emphasis)
    - [Lists](#lists)
      - [Unordered](#unordered)
      - [Ordered](#ordered)
    - [Images](#images)
    - [Links](#links)
    - [Blockquotes](#blockquotes)
    - [Inline code](#inline-code)

Table of contents generated.
```

Only generate 2-3 title levels:

```bash
$ python3 md-toc.py examples/Mastering_Markdown.md -o -s 2 -e 3
Generate from file: examples/Mastering_Markdown.md

- [What is Markdown?](#what-is-markdown)
- [Examples](#examples)
- [Syntax guide](#syntax-guide)
  - [Headers](#headers)
  - [Emphasis](#emphasis)
  - [Lists](#lists)
  - [Images](#images)
  - [Links](#links)
  - [Blockquotes](#blockquotes)
  - [Inline code](#inline-code)

Table of contents generated.
```

#### Write results to a file or print to standard output

By default, the program automatically writes the generated **TOC** to the beginning of the original file.

Add the option `-o` or `--output` when you want to print the results to standard output for copying or other processing.

```bash
-o, --output          print toc to stdout instead of writing to file
```

Use the `>` on the command line to export the generated directory to a separate file:

```bash
$ python3 md-toc.py -o README.md > table_of_content.md
```

## Dependency

- Python3

Tested on Ubuntu 18.04 in bash with Python 3.6.7.