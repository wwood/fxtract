CXX=g++
LIBS=
CXXFLAGS=-Wall -O2
EXECUTABLE=fxtract
SEQAN=../third_party/seqan-1.4.1/include

ifdef ZLIB
	override CXXFLAGS := $(CXXFLAGS) -DSEQAN_HAS_ZLIB
	override LIBS := $(LIBS) -lz
endif

ifdef BZIP2
	override CXXFLAGS := $(CXXFLAGS) -DSEQAN_HAS_BZIP2
	override LIBS := $(LIBS) -lbz2
endif

ifdef DEBUG
	override CXXFLAGS := $(CXXFLAGS) -ggdb
endif

all: main.o fileManager.o $(EXECUTABLE)

clean:
	rm main.o fileManager.o fxtract

test: $(EXECUTABLE)
	cd ../test/
	./run.sh


main.o: main.cpp util.h
	$(CXX) -c $(CXXFLAGS) -I$(SEQAN) $< -o $@

fileManager.o: fileManager.cpp fileManager.h
	$(CXX) -c $(CXXFLAGS) -I$(SEQAN) $< -o $@

$(EXECUTABLE): main.o fileManager.o
	$(CXX) $(CXXFLAGS) -I$(SEQAN) -o $(EXECUTABLE) $^ $(LIBS)
