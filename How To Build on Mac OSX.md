##How to Build on Mac OSX
### Install Environments
1. You need MacTex to compile tex project. [Download MacTex](http://tug.org/cgi-bin/mactex-download/MacTeX.pkg).
2. This project uses `Pygments` as syntax highlighter. You can get it from the [Python Package Index](https://pypi.python.org/pypi/Pygments), or install it with: `pip install Pygments`(`pip` is a tool for installing Python packages, you can get it from [here](https://pypi.python.org/pypi/pip/)).
3. After you have installed MacTex and Pygments, please install the fonts: 
	* `fonts/AdobeSongStd-Light (v5.010).otf`
	* `fonts/AdobeKaitiStd-Regular (v5.010).otf`
	* `fonts/AdobeHeitiStd-Regular (v5.010).otf`
	* `fonts/AdobeFangsongStd-Regular.otf`  
  
  Just double click the font files and then click “install font” at the bottom of the preview, to install font into your OSX.
4. If you do not have the dictionary `~/Library/texmf`, use this [tool](https://www.msu.edu/~amunn/latex/make-local-texmf.zip) to create it.
5. run these commends to install tex package `minted`:  

	```shell
	sudo wget http://mirrors.ctan.org/macros/latex/contrib/minted.zip
	sudo unzip minted.zip
	cd minted/
	sudo make
	sudo mv ~/Library/texmf/tex/latex/minted/minted.sty ~/Library/texmf/tex/latex/minted/minted.sty.backup
	sudo mv minted.sty ~/Library/texmf/tex/latex/minted
	sudo mv minted1.sty ~/Library/texmf/tex/latex/minted
	cd ..
	sudo rm -rf minted
	sudo rm minted.zip
	
	``` 

After these 5 steps, you have had the environment to build this project.

### Build to PDF
Each time before build it, make sure the three lines as follow in `guide-book.tex` (their line numbers are 29~31) are uncommented:

```latex
%\setCJKmainfont[BoldFont={AdobeHeitiStd-Regular},ItalicFont={AdobeKaitiStd-Regular}]{AdobeSongStd-Light}
%\setCJKsansfont[BoldFont={AdobeHeitiStd-Regular}]{AdobeKaitiStd-Regular}
%\setCJKmonofont{AdobeFangsongStd-Regular}
```

Then, you can build with the commond as follow:

```shell
cd guide-book
make
```
Then you well get the `guide-book.pdf` in the dictionary `guide-book`.

### Before Push to Travis-CI
Before push this repository to Travis-CI, remember to comment out the three lines in `guide-book.tex`:

```latex
\setCJKmainfont[BoldFont={AdobeHeitiStd-Regular},ItalicFont={AdobeKaitiStd-Regular}]{AdobeSongStd-Light}
\setCJKsansfont[BoldFont={AdobeHeitiStd-Regular}]{AdobeKaitiStd-Regular}
\setCJKmonofont{AdobeFangsongStd-Regular}
```


