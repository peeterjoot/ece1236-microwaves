THISDIR := ece1236-microwaves
THISBOOK := ece1236

BIBLIOGRAPHY_PATH := classicthesis_mine
HAVE_OWN_CONTENTS := 1
#HAVE_OWN_TITLEPAGE := 1
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/Index.tex
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/ContentsAndFigures.tex
BOOKTEMPLATE := ../latex/classicthesis_mine/ClassicThesis2.tex

include make.revision
include ../latex/make.bookvars

#ONCEFLAGS := -justonce

SOURCE_DIRS += appendix
FIGURES := ../figures/ece1236-microwaves
SOURCE_DIRS += $(FIGURES)

GENERATED_SOURCES += matlab.tex 
GENERATED_SOURCES += mathematica.tex 
GENERATED_SOURCES += julia.tex 
GENERATED_SOURCES += backmatter.tex
 
EPS_FILES := $(wildcard $(FIGURES)/*.eps)
PDFS_FROM_EPS := $(subst eps,pdf,$(EPS_FILES))

THISBOOK_DEPS += $(PDFS_FROM_EPS)
#THISBOOK_DEPS += macros_mathematica.sty
DO_SPELL_CHECK := $(shell cat spellcheckem.txt)

include ../latex/make.rules

.PHONY: spellcheck
spellcheck: $(patsubst %.tex,%.sp,$(filter-out $(DONT_SPELL_CHECK),$(DO_SPELL_CHECK)))

%.sp : %.tex
	spellcheck $^
	touch $@

julia.tex : ../julia/METADATA
mathematica.tex : ../mathematica/METADATA
matlab.tex : ../matlab/METADATA

#uwaves4TransmissionLines.pdf : ../ece1236/uwaves4TransmissionLinesCore.tex
#uwavesDeck5SmithChart.pdf :: ../ece1236/uwavesDeck5SmithChartCore.tex
#uwavesDeck7MultisectionTransformers.pdf : ../ece1236/uwavesDeck7MultisectionTransformersCore.tex

#problemSets :: uwavesproblemSet1.pdf
#
#ps7mathematica.tex : ../METADATA ../mathematica/METADATA
#	(cd .. ; ./METADATA -mathematica -latex -ece1236 -filter ece1236/ps7/ ) > $@
#
#ps8mathematica.tex : ../METADATA ../mathematica/METADATA
#	(cd .. ; ./METADATA -mathematica -latex -ece1236 -filter ece1236/ps8/ ) > $@

#backmatter.tex: ../latex/classicthesis_mine/backmatter_with_parts.tex
#	rm -f $@
#	ln -s ../latex/classicthesis_mine/backmatter_with_parts.tex backmatter.tex

backmatter.tex: ../latex/classicthesis_mine/backmatter_with_parts.tex
	rm -f $@
	ln -s ../latex/classicthesis_mine/backmatter2.tex backmatter.tex
