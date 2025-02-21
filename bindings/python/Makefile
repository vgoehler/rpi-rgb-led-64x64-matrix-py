# Exectuables
PIP	   = pip
INST_ARGS  := install .
ifdef DESTDIR
INST_ARGS  += --root=$(DESTDIR)
endif

# Where our library resides. It is split between includes and the binary
# library in lib
RGB_LIBDIR=../../lib
RGB_LIBRARY_NAME=rgbmatrix
RGB_LIBRARY=$(RGB_LIBDIR)/lib$(RGB_LIBRARY_NAME).a

all: build
build: build-python
install: install-python
clean: clean-python
	find ./rgbmatrix -type f -name \*.so -delete
	find . -type f -name \*.pyc -delete

$(RGB_LIBRARY): FORCE
	$(MAKE) -C $(RGB_LIBDIR)

# install step does all the building for python with pip
build-python: $(RGB_LIBRARY)
	$(MAKE) -C rgbmatrix

install-python: build-python
	$(PIP) $(INST_ARGS)

clean-python:
	$(RM) -r build dist *.egg-info

FORCE:
.PHONY: FORCE
.PHONY: build install clean
.PHONY: build-python install-python clean-python
