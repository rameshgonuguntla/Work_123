public void givenMap_whenGetPut500ktimes_ConcurrentFaster(){

Map hashMap = new HashMap();
Map synHashMap1 = Collections.synchronizedMap(new HashMap<>());
Map concurrentMap = new ConcurrentHashMap<>();

Integer threadCount = 50;
Integer iterations = 1000000;
Long timeMap = getTimeElapsed(hashMap, threadCount, iterations);
System.out.println(” Map time elapsed milli “+ timeMap);
Long timeSynchMap = getTimeElapsed(synHashMap1, threadCount, iterations);
System.out.println(” SynchonizedMap time elapsed milli “+ timeSynchMap);
Long timeConcurrentMap = getTimeElapsed(concurrentMap, threadCount, iterations);
System.out.println(” ConcurrentMap time elapsed milli” +
” “+ timeConcurrentMap);
System.out.println(“Map:”+timeMap+”,Synch Map:”+timeSynchMap+”,Concurrent Map:”+timeConcurrentMap);
assertTrue(timeMap > timeSynchMap && timeMap > timeConcurrentMap);

}