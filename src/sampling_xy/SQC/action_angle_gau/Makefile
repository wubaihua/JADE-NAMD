#
# Paths to directories commands
#
DIR = ./
INCDIR = ${DIR}/include
#
# UNIX commands
#
CP    = /bin/cp -f
RM    = /bin/rm -f
MKEXE = /bin/chmod 755
AR    = /usr/bin/ar
#
# Libraries
#
# LIB = -lblas
#LIB =   -llapack -lblas
#
# Compilers
#
F90C = gfortran
#F90C = ifort
#F90C = pgf90
#F90FLAGS = -C -CB
#F90FLAGS = -O3 -stand f03 -check all -traceback -warn all -fstack-protector -assume protect_parens -implicitnone
#F90FLAGS = -FR -O3 -I${INCDIR}
#F90FLAGS =    -Mbounds -I${INCDIR}
#F90FLAGS = -g -Mbounds -I${INCDIR} -fpic
#F90FLAGS =  -fastsse -tp athlonxp -I${INCDIR}
FC = gfortran
#FC = ifort
#FC = pgf90
#FFLAGS = -g -Mbounds -I${INCDIR} -fpic
#FFLAGS = -l lapack -l f77blas -l atlas
#FFLAGS = -O3   

 CC = gcc
#CFLAGS = -O3    
RUNAR = ar rv
#
# Executable, source and objects
#
EXE  = main_action_angle_gau.exe
#EXE = testfft.exe
ARCHI = ${DIR}/${EXE:.exe=.a}
MAIN = ${EXE:.exe=.f90}

#FSRC = read_tool.o

F90SRC = sub_random_gau_1d.o

CSRC = 

#
# Dependencies
#
${ARCHI}: ${FSRC} ${F90SRC} ${CSRC}
	${AR} rv ${ARCHI} *.o

${EXE}: ${ARCHI} ${MAIN}
	${AR} rv ${ARCHI} *.o
	${F90C}  -o  $@ ${F90FLAGS} ${MAIN} ${ARCHI} ${LIB}  

install: ${EXE} 
#	cp ${EXE} sampling.x
#	mv ${EXE} ../../bin/sampling2.x
	${RM} *.o


clean:
	${RM} *.o

veryclean:
	${RM} ${EXE} *.o ${ARCHI}

#
# Suffix rules
#
.SUFFIXES: $(SUFFIXES) .f90
.f90.o:
	${F90C} -c ${F90FLAGS} $*.f90
.f.o:
	${FC} -c ${FFLAGS} $*.f
	
.c.o:
	${CC} -c ${CFLAGS} $*.c
