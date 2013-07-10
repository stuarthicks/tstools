
cmake_minimum_required( VERSION 2.8 )

project( tstools )

include_directories( 
	
)

################################################################
#############		MACRO DEFINITION			################
################################################################

macro( add_executable_oneline name )

	add_executable( ${name} ${ARGN} version.h )
	target_link_libraries( ${name} tstools )

endmacro()

macro( add_test_oneline test_name )

	add_executable_oneline( ${test_name} ${ARGN} )
	add_test( ${test_name} ${test_name} )

endmacro()

################################################################
#############			COMPONENTS				################
################################################################

set( LIBTSTOOLS_SRC
	ac3.c
	ac3_fns.h
	accessunit.c
	accessunit_defns.h
	accessunit_fns.h
	adts.c
	adts_defns.h
	adts_fns.h
	audio.c
	audio_defns.h
	audio_fns.h
	avs.c
	avs_defns.h
	avs_fns.h
	bitdata.c
	bitdata_defns.h
	bitdata_fns.h
	compat.h
	es.c
	es_defns.h
	es_fns.h
	ethernet.c
	ethernet.h
	filter.c
	filter_defns.h
	filter_fns.h
	fmtx.c
	fmtx.h
	h222.c
	h222_defns.h
	h222_fns.h
	h262.c
	h262_defns.h
	h262_fns.h
	ipv4.c
	ipv4.h
	l2audio.c
	l2audio_fns.h
	misc.c
	misc_defns.h
	misc_fns.h
	nalunit.c
	nalunit_defns.h
	nalunit_fns.h
	pcap.c
	pcap.h
	pes.c
	pes_defns.h
	pes_fns.h
	pidint.c
	pidint_defns.h
	pidint_fns.h
	printing.c
	printing_defns.h
	printing_fns.h
	ps.c
	ps_defns.h
	ps_fns.h
	reverse.c
	reverse_defns.h
	reverse_fns.h
	ts.c
	ts_defns.h
	ts_fns.h
	tsplay_defns.h
	tsplay_fns.h
	tsplay_innards.c
	tswrite.c
	tswrite_defns.h
	tswrite_fns.h
	version.h
	video_defns.h
)

################################################################
#############			TARGETS					################
################################################################

add_library( tstools ${LIBTSTOOLS_SRC} )
add_executable_oneline( es2ts es2ts.c )
add_executable_oneline( esdots esdots.c )
add_executable_oneline( esfilter esfilter.c )
add_executable_oneline( esreport esreport.c )
add_executable_oneline( esmerge esmerge.c )
add_executable_oneline( esreverse esreverse.c )
add_executable_oneline( psreport psreport.c )
add_executable_oneline( psdots psdots.c )
add_executable_oneline( ps2ts ps2ts.c )
add_executable_oneline( stream_type stream_type.c )
add_executable_oneline( ts2es ts2es.c )
add_executable_oneline( ts2ps ts2ps.c )
add_executable_oneline( tsdvbsub tsdvbsub.c )
add_executable_oneline( tsinfo tsinfo.c )
add_executable_oneline( tsreport tsreport.c )
add_executable_oneline( tsserve tsserve.c )
add_executable_oneline( ts_packet_insert ts_packet_insert.c )
add_executable_oneline( tsplay tsplay.c )
add_executable_oneline( m2ts2ts m2ts2ts.c )
add_executable_oneline( pcapreport pcapreport.c )
add_executable_oneline( tsfilter tsfilter.c )

################################################################
#############				TESTS				################
################################################################

enable_testing()

add_test_oneline( test_pes test_pes.c )
# add_test_oneline( test_printing test_printing.c )
# add_test_oneline( test_ps test_ps.c ${PS_H} ${MISC_H} version.h )
add_test_oneline( test_nal_unit_list test_nal_unit_list.c )
add_test_oneline( test_es_unit_list test_es_unit_list.c )

################################################################
#############		INSTALL RULES				################
################################################################

# install( TARGETS ... DESTINATION bin )
