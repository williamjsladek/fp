<template>
  <div class="fish">
    <h3>Fish</h3>
    <div>
        <p v-if="loading" class="text-danger">
            PLEASE WAIT... LOADING
        </p>
        <div v-if="!loading">
            <p>
                Unfortunately, due to an incomplete api, fish data is only shown for counties Annapolis, Antigonish, Cape Breton, Colchester, and Cumberland.
            </p>
            <p>
                We appologize for this inconvenience.
            </p>
            <p>
                Please select which items you wish to view.
            </p>
            <div>
                <input type="button" @click.prevent="reset()" value="Hide All"/>
                <input type="button" @click.prevent="showAll()" value="Show All"/>
            </div>
            <br/>
            <div>
                <input type="button" @click.prevent="Ap()" value="Show/Hide Annapolis"/>
                <input type="button" @click.prevent="At()" value="Show/Hide Antigonish"/>
                <input type="button" @click.prevent="Cb()" value="Show/Hide Cape Breton"/>
                <input type="button" @click.prevent="Cch()" value="Show/Hide Colchester"/>
                <input type="button" @click.prevent="Cm()" value="Show/Hide Cumberland"/>
            </div>
            <br/>
            <div>
                <input type="button" @click.prevent="bandedKillfish()" value="Show/Hide Banded Killfish"/>
                <input type="button" @click.prevent="yellowPerch()" value="Show/Hide Yellow Perch"/>
                <input type="button" @click.prevent="brownBullhead()" value="Show/Hide Brown Bullhead"/>
                <input type="button" @click.prevent="whiteSucker()" value="Show/Hide White Sucker"/>
                <input type="button" @click.prevent="goldenShiner()" value="Show/Hide Golden Shiner"/>
                <input type="button" @click.prevent="americanEel()" value="Show/Hide American Eel"/>
                <input type="button" @click.prevent="brookTrout()" value="Show/Hide Brook Trout"/>
                <input type="button" @click.prevent="whitePerch()" value="Show/Hide White Perch"/>
                <input type="button" @click.prevent="smallmouthBass()" value="Show/Hide Smallmouth Bass"/>
                <input type="button" @click.prevent="creekChub()" value="Show/Hide Creek Chub"/>
                <input type="button" @click.prevent="lakeWhitefish()" value="Show/Hide Lake Whitefish"/>
                <input type="button" @click.prevent="threeSpineStickleback()" value="Show/Hide Three-Spine Stickleback"/>
                <input type="button" @click.prevent="fourSpineStickleback()" value="Show/Hide Four-Spine Stickleback"/>
                <input type="button" @click.prevent="lakeChub()" value="Show/Hide Lake Chub"/>
                <input type="button" @click.prevent="stripedBass()" value="Show/Hide Striped Bass"/>
                <input type="button" @click.prevent="commonShiner()" value="Show/Hide Common Shiner"/>
                <input type="button" @click.prevent="atlanticSalmon()" value="Show/Hide Atlantic Salmon"/>
                <input type="button" @click.prevent="brownTrout()" value="Show/Hide Brown Trout"/>
                <input type="button" @click.prevent="tigerTrout()" value="Show/Hide Tiger Trout"/>
                <input type="button" @click.prevent="rainbowTrout()" value="Show/Hide RainbowTrout"/>
                <input type="button" @click.prevent="nineSpineStickleback()" value="Show/Hide Nine-Spine Stickleback"/>
                <input type="button" @click.prevent="alewife()" value="Show/Hide Alewife"/>
                <input type="button" @click.prevent="chainPickerel()" value="Show/Hide Chain Pickerel"/>
                <input type="button" @click.prevent="atlanticSilverside()" value="Show/Hide Atlantic Silverside"/>
                <input type="button" @click.prevent="mummichog()" value="Show/Hide Mummichog"/>
               <input type="button" @click.prevent="blackNoseDace()" value="Show/Hide Black Nose Dace"/>
                <input type="button" @click.prevent="tomcod()" value="Show/Hide Tomcod"/>
            </div>
            <table>
                <tr>
                    <td v-if="(ap&&BandedKillfish)||(ap&&allFishFalse())||(BandedKillfish&&allCountiesFalse)">This would show the count for Banded Killfish caught in Annapolis</td>
                    <td v-if="(at&&BandedKillfish)||(at&&allFishFalse())||(BandedKillfish&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&BandedKillfish)||(cb&&allFishFalse())||(BandedKillfish&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&BandedKillfish)||(cch&&allFishFalse())||(BandedKillfish&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&BandedKillfish)||(cm&&allFishFalse())||(BandedKillfish&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&YellowPerch)||(ap&&allFishFalse())||(YellowPerch&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&YellowPerch)||(at&&allFishFalse())||(YellowPerch&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&YellowPerch)||(cb&&allFishFalse())||(YellowPerch&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&YellowPerch)||(cch&&allFishFalse())||(YellowPerch&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&YellowPerch)||(cm&&allFishFalse())||(YellowPerch&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&BrownBullhead)||(ap&&allFishFalse())||(BrownBullhead&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&BrownBullhead)||(at&&allFishFalse())||(BrownBullhead&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&BrownBullhead)||(cb&&allFishFalse())||(BrownBullhead&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&BrownBullhead)||(cch&&allFishFalse())||(BrownBullhead&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&BrownBullhead)||(cm&&allFishFalse())||(BrownBullhead&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&WhiteSucker)||(ap&&allFishFalse())||(WhiteSucker&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&WhiteSucker)||(at&&allFishFalse())||(WhiteSucker&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&WhiteSucker)||(cb&&allFishFalse())||(WhiteSucker&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&WhiteSucker)||(cch&&allFishFalse())||(WhiteSucker&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&WhiteSucker)||(cm&&allFishFalse())||(WhiteSucker&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&GoldenShiner)||(ap&&allFishFalse())||(GoldenShiner&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&GoldenShiner)||(at&&allFishFalse())||(GoldenShiner&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&GoldenShiner)||(cb&&allFishFalse())||(GoldenShiner&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&GoldenShiner)||(cch&&allFishFalse())||(GoldenShiner&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&GoldenShiner)||(cm&&allFishFalse())||(GoldenShiner&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&AmericanEel)||(ap&&allFishFalse())||(AmericanEel&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&AmericanEel)||(at&&allFishFalse())||(AmericanEel&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&AmericanEel)||(cb&&allFishFalse())||(AmericanEel&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&AmericanEel)||(cch&&allFishFalse())||(AmericanEel&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&AmericanEel)||(cm&&allFishFalse())||(AmericanEel&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&BrookTrout)||(ap&&allFishFalse())||(BrookTrout&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&BrookTrout)||(at&&allFishFalse())||(BrookTrout&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&BrookTrout)||(cb&&allFishFalse())||(BrookTrout&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&BrookTrout)||(cch&&allFishFalse())||(BrookTrout&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&BrookTrout)||(cm&&allFishFalse())||(BrookTrout&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&WhitePerch)||(ap&&allFishFalse())||(WhitePerch&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&WhitePerch)||(at&&allFishFalse())||(WhitePerch&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&WhitePerch)||(cb&&allFishFalse())||(WhitePerch&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&WhitePerch)||(cch&&allFishFalse())||(WhitePerch&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&WhitePerch)||(cm&&allFishFalse())||(WhitePerch&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&SmallmouthBass)||(ap&&allFishFalse())||(SmallmouthBass&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&SmallmouthBass)||(at&&allFishFalse())||(SmallmouthBass&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&SmallmouthBass)||(cb&&allFishFalse())||(SmallmouthBass&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&SmallmouthBass)||(cch&&allFishFalse())||(SmallmouthBass&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&SmallmouthBass)||(cm&&allFishFalse())||(SmallmouthBass&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&CreekChub)||(ap&&allFishFalse())||(CreekChub&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&CreekChub)||(at&&allFishFalse())||(CreekChub&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&CreekChub)||(cb&&allFishFalse())||(CreekChub&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&CreekChub)||(cch&&allFishFalse())||(CreekChub&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&CreekChub)||(cm&&allFishFalse())||(CreekChub&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&LakeWhitefish)||(ap&&allFishFalse())||(LakeWhitefish&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&LakeWhitefish)||(at&&allFishFalse())||(LakeWhitefish&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&LakeWhitefish)||(cb&&allFishFalse())||(LakeWhitefish&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&LakeWhitefish)||(cch&&allFishFalse())||(LakeWhitefish&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&LakeWhitefish)||(cm&&allFishFalse())||(LakeWhitefish&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&ThreeSpinesStickleback)||(ap&&allFishFalse())||(ThreeSpinesStickleback&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&ThreeSpinesStickleback)||(at&&allFishFalse())||(ThreeSpinesStickleback&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&ThreeSpinesStickleback)||(cb&&allFishFalse())||(ThreeSpinesStickleback&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&ThreeSpinesStickleback)||(cch&&allFishFalse())||(ThreeSpinesStickleback&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&ThreeSpinesStickleback)||(cm&&allFishFalse())||(ThreeSpinesStickleback&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&FourSpinesStickleback)||(ap&&allFishFalse())||(FourSpinesStickleback&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&FourSpinesStickleback)||(at&&allFishFalse())||(FourSpinesStickleback&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&FourSpinesStickleback)||(cb&&allFishFalse())||(FourSpinesStickleback&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&FourSpinesStickleback)||(cch&&allFishFalse())||(FourSpinesStickleback&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&FourSpinesStickleback)||(cm&&allFishFalse())||(FourSpinesStickleback&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&LakeChub)||(ap&&allFishFalse())||(LakeChub&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&LakeChub)||(at&&allFishFalse())||(LakeChub&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&LakeChub)||(cb&&allFishFalse())||(LakeChub&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&LakeChub)||(cch&&allFishFalse())||(LakeChub&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&LakeChub)||(cm&&allFishFalse())||(LakeChub&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&StripedBass)||(ap&&allFishFalse())||(StripedBass&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&StripedBass)||(at&&allFishFalse())||(StripedBass&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&StripedBass)||(cb&&allFishFalse())||(StripedBass&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&StripedBass)||(cch&&allFishFalse())||(StripedBass&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&StripedBass)||(cm&&allFishFalse())||(StripedBass&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&CommonShiner)||(ap&&allFishFalse())||(CommonShiner&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&CommonShiner)||(at&&allFishFalse())||(CommonShiner&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&CommonShiner)||(cb&&allFishFalse())||(CommonShiner&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&CommonShiner)||(cch&&allFishFalse())||(CommonShiner&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&CommonShiner)||(cm&&allFishFalse())||(CommonShiner&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&AtlanticSalmon)||(ap&&allFishFalse())||(AtlanticSalmon&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&AtlanticSalmon)||(at&&allFishFalse())||(AtlanticSalmon&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&AtlanticSalmon)||(cb&&allFishFalse())||(AtlanticSalmon&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&AtlanticSalmon)||(cch&&allFishFalse())||(AtlanticSalmon&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&AtlanticSalmon)||(cm&&allFishFalse())||(AtlanticSalmon&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&BrownTrout)||(ap&&allFishFalse())||(BrownTrout&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&BrownTrout)||(at&&allFishFalse())||(BrownTrout&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&BrownTrout)||(cb&&allFishFalse())||(BrownTrout&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&BrownTrout)||(cch&&allFishFalse())||(BrownTrout&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&BrownTrout)||(cm&&allFishFalse())||(BrownTrout&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&TigerTrout)||(ap&&allFishFalse())||(TigerTrout&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&TigerTrout)||(at&&allFishFalse())||(TigerTrout&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&TigerTrout)||(cb&&allFishFalse())||(TigerTrout&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&TigerTrout)||(cch&&allFishFalse())||(TigerTrout&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&TigerTrout)||(cm&&allFishFalse())||(TigerTrout&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&RainbowTrout)||(ap&&allFishFalse())||(RainbowTrout&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&RainbowTrout)||(at&&allFishFalse())||(RainbowTrout&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&RainbowTrout)||(cb&&allFishFalse())||(RainbowTrout&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&RainbowTrout)||(cch&&allFishFalse())||(RainbowTrout&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&RainbowTrout)||(cm&&allFishFalse())||(RainbowTrout&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&NineSpineSickleback)||(ap&&allFishFalse())||(NineSpineSickleback&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&NineSpineSickleback)||(at&&allFishFalse())||(NineSpineSickleback&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&NineSpineSickleback)||(cb&&allFishFalse())||(NineSpineSickleback&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&NineSpineSickleback)||(cch&&allFishFalse())||(NineSpineSickleback&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&NineSpineSickleback)||(cm&&allFishFalse())||(NineSpineSickleback&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&Alewife)||(ap&&allFishFalse())||(Alewife&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&Alewife)||(at&&allFishFalse())||(Alewife&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&Alewife)||(cb&&allFishFalse())||(Alewife&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&Alewife)||(cch&&allFishFalse())||(Alewife&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&Alewife)||(cm&&allFishFalse())||(Alewife&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&ChainPickerel)||(ap&&allFishFalse())||(ChainPickerel&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&ChainPickerel)||(at&&allFishFalse())||(ChainPickerel&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&ChainPickerel)||(cb&&allFishFalse())||(ChainPickerel&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&ChainPickerel)||(cch&&allFishFalse())||(ChainPickerel&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&ChainPickerel)||(cm&&allFishFalse())||(ChainPickerel&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&AtlanticSilverside)||(ap&&allFishFalse())||(AtlanticSilverside&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&AtlanticSilverside)||(at&&allFishFalse())||(AtlanticSilverside&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&AtlanticSilverside)||(cb&&allFishFalse())||(AtlanticSilverside&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&AtlanticSilverside)||(cch&&allFishFalse())||(AtlanticSilverside&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&AtlanticSilverside)||(cm&&allFishFalse())||(AtlanticSilverside&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&Mummichog)||(ap&&allFishFalse())||(Mummichog&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&Mummichog)||(at&&allFishFalse())||(Mummichog&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&Mummichog)||(cb&&allFishFalse())||(Mummichog&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&Mummichog)||(cch&&allFishFalse())||(Mummichog&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&Mummichog)||(cm&&allFishFalse())||(Mummichog&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&BlackNoseDace)||(ap&&allFishFalse())||(BlackNoseDace&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&BlackNoseDace)||(at&&allFishFalse())||(BlackNoseDace&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&BlackNoseDace)||(cb&&allFishFalse())||(BlackNoseDace&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&BlackNoseDace)||(cch&&allFishFalse())||(BlackNoseDace&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&BlackNoseDace)||(cm&&allFishFalse())||(BlackNoseDace&&allCountiesFalse)">Test 5</td>
                </tr>
                <tr>
                    <td v-if="(ap&&Tomcod)||(ap&&allFishFalse())||(Tomcod&&allCountiesFalse)">Test 1</td>
                    <td v-if="(at&&Tomcod)||(at&&allFishFalse())||(Tomcod&&allCountiesFalse)">Test 2</td>
                    <td v-if="(cb&&Tomcod)||(cb&&allFishFalse())||(Tomcod&&allCountiesFalse)">Test 3</td>
                    <td v-if="(cch&&Tomcod)||(cch&&allFishFalse())||(Tomcod&&allCountiesFalse)">Test 4</td>
                    <td v-if="(cm&&Tomcod)||(cm&&allFishFalse())||(Tomcod&&allCountiesFalse)">Test 5</td>
                </tr>
            </table>
        </div>
    </div>
  </div>
</template>

<style>
.fish {
    margin: auto;
}
table {
    margin: auto;
}
td {
    padding: 5px;
}
tr {
    padding: 10px;
}
</style>

<script>
import axios from 'axios'
//import ToggleButton from 'vue-js-toggle-button'

export default {
  name: 'Fish',
  data () {
    return {
        loading: false,
        fishData: [],
        Default: true,
        ap: false,
        at: false,
        cb: false,
        cch: false,
        cm: false,
        //county: false,
        BandedKillfish: false,
        YellowPerch: false,
        BrownBullhead: false,
        WhiteSucker: false,
        GoldenShiner: false,
        AmericanEel: false,
        BrookTrout: false,
        WhitePerch: false,
        SmallmouthBass: false,
        CreekChub: false,
        LakeWhitefish: false,
        ThreeSpineStickleback: false,
        FourSpineStickleback: false,
        LakeChub: false,
        StripedBass: false,
        CommonShiner: false,
        AtlanticSalmon: false,
        BrownTrout: false,
        TigerTrout: false,
        RainbowTrout: false,
        NineSpineStickleback: false,
        Alewife: false,
        ChainPickerel: false,
        AtlanticSilverside: false,
        Mummichog: false,
        BlackNoseDace: false,
        Tomcod: false,
        //fish: false,

    }
  },
  methods:{
    async getFishData () {
      this.loading = true;
      try {
        let url = 'https://data.novascotia.ca/resource/jgyj-d4fh.json';
        axios.get(url)
          .then(response => {
            this.fishData = response.data
          })
          .catch(error => {
            console.log(error)
            this.errored = true
          })
          .finally(() => {
            this.loading = false
            console.log(this.fishData)
            }
        )
      } catch (err) {
        console.log(err);
      }
    }, 

    setCountiesFalse ()
    {
        this.ap = false
        this.at = false
        this.cb = false
        this.cch = false
        this.cm = false
        //this.county = false
    },

    allCountiesFalse()
    {
        return (!(this.app || this.at || this.cb || this.cch || this.cm))
    },

    setFishFalse()
    {
        
        this.BandedKillfish = false
        this.YellowPerch = false
        this.BrownBullhead = false
        this.WhiteSucker = false
        this.GoldenShiner = false
        this.AmericanEel = false
        this.BrookTrout = false
        this.WhitePerch = false
        this.SmallmouthBass = false
        this.CreekChub = false
        this.LakeWhitefish = false
        this.ThreeSpineStickleback = false
        this.FourSpineStickleback = false
        this.LakeChub = false
        this.StripedBass = false
        this.CommonShiner = false
        this.AtlanticSalmon = false
        this.BrownTrout = false
        this.TigerTrout = false
        this.RainbowTrout = false
        this.NineSpineStickleback = false
        this.Alewife = false
        this.ChainPickerel = false
        this.AtlanticSilverside = false
        this.Mummichog = false
        this.BlackNoseDace = false
        this.Tomcod = false
        //this.fish || 
    },
    
    allFishFalse() 
    {
        return (!(this.BandedKillfish || this.YellowPerch || this.BrownBullhead || this.WhiteSucker || this.GoldenShiner || this.AmericanEel || this.BrookTrout || 
        this.WhitePerch || this.SmallmouthBass || this.CreekChub || this.LakeWhitefish || this.ThreeSpineStickleback || this.FourSpineStickleback || this.LakeChub || 
        this.StripedBass || this.CommonShiner || this.AtlanticSalmon || this.BrownTrout || this.TigerTrout || this.RainbowTrout || this.NineSpineStickleback || this.Alewife || 
        this.ChainPickerel || this.AtlanticSilverside || this.Mummichog || this.BlackNoseDace || this.Tomcod))
    },

    setCountiesTrue ()
    {
        this.ap = true
        this.at = true
        this.cb = true
        this.cch = true
        this.cm = true
        //this.county = true
    },
    
    allCountiesTrue()
    {
        return((this.ap && this.at && this.cb && this.cch && this.cm))
    },

    setFishTrue()
    {
        
        this.BandedKillfish = true
        this.YellowPerch = true
        this.BrownBullhead = true
        this.WhiteSucker = true
        this.GoldenShiner = true
        this.AmericanEel = true
        this.BrookTrout = true
        this.WhitePerch = true
        this.SmallmouthBass = true
        this.CreekChub = true
        this.LakeWhitefish = true
        this.ThreeSpineStickleback = true
        this.FourSpineStickleback = true
        this.LakeChub = true
        this.StripedBass = true
        this.CommonShiner = true
        this.AtlanticSalmon = true
        this.BrownTrout = true
        this.TigerTrout = true
        this.RainbowTrout = true
        this.NineSpineStickleback = true
        this.Alewife = true
        this.ChainPickerel = true
        this.AtlanticSilverside = true
        this.Mummichog = true
        this.BlackNoseDace = true
        this.Tomcod = true
        //this.fish = true
    },
    
    allFishTrue() 
    {
        return ((this.BandedKillfish && this.YellowPerch && this.BrownBullhead && this.WhiteSucker && this.GoldenShiner && this.AmericanEel && this.BrookTrout && 
        this.WhitePerch && this.SmallmouthBass && this.CreekChub && this.LakeWhitefish && this.ThreeSpineStickleback && this.FourSpineStickleback && this.LakeChub && 
        this.StripedBass && this.CommonShiner && this.AtlanticSalmon && this.BrownTrout && this.TigerTrout && this.RainbowTrout && this.NineSpineStickleback && this.Alewife && 
        this.ChainPickerel && this.AtlanticSilverside && this.Mummichog && this.BlackNoseDace && this.Tomcod))
    },

    reset()
    {
        this.setCountiesFalse()
        this.setFishFalse()
    },
    showAll()
    {
        this.setCountiesTrue()
        this.setFishTrue()
    },

    Ap()
    {
        this.ap = !this.ap
    },
    At()
    {
        this.at = !this.at
    },
    Cb()
    {
        this.cb = !this.cb
    },
    Cch()
    {
        this.cch = !this.cch
    },
    Cm()
    {
        this.cm = !this.cm
    },

    bandedKillfish()
    {
        this.BandedKillfish = !this.BandedKillfish
    },
    yellowPerch()
    {
        this.YellowPerch = !this.YellowPerch
    },
    brownBullhead()
    {
        this.BrownBullhead = !this.BrownBullhead
    },
    whiteSucker()
    {
        this.WhiteSucker = !this.WhiteSucker
    },
    goldenShiner()
    {
        this.GoldenShiner = !this.GoldenShiner
    },
    americanEel()
    {
        this.AmericanEel = !this.AmericanEel
    },
    brookTrout()
    {
        this.BrookTrout = !this.BrookTrout
    },
    whitePerch()
    {
        this.WhitePerch = !this.WhitePerch
    },
    smallmouthBass()
    {
        this.SmallmouthBass = !this.SmallmouthBass
    },
    creekChub()
    {
        this.CreekChub = !this.CreekChub
    },
    lakeWhitefish()
    {
        this.LakeWhitefish = !this.LakeWhitefish
    },
    threeSpineStickleback()
    {
        this.ThreeSpineStickleback = !this.ThreeSpineStickleback
    },
    fourSpineStickleback()
    {
        this.FourSpineStickleback = !this.FourSpineStickleback
    },
    lakeChub()
    {
        this.LakeChub = !this.LakeChub
    },
    stripedBass()
    {
        this.StripedBass = !this.StripedBass
    },
    commonShiner()
    {
        this.CommonShiner = !this.CommonShiner
    },
    atlanticSalmon()
    {
        this.AtlanticSalmon = !this.AtlanticSalmon
    },
    brownTrout()
    {
        this.BrownTrout = !this.BrownTrout
    },
    tigerTrout()
    {
        this.TigerTrout = !this.TigerTrout
    },
    rainbowTrout()
    {
        this.RainbowTrout = !this.RainbowTrout
    },
    nineSpineStickleback()
    {
        this.NineSpineStickleback = !this.NineSpineStickleback
    },
    alewife()
    {
        this.Alewife = !this.Alewife
    },
    chainPickerel()
    {
        this.ChainPickerel = !this.ChainPickerel
    },
    atlanticSilverside()
    {
        this.AtlanticSilverside = !this.AtlanticSilverside
    },
    mummichog()
    {
        this.Mummichog = !this.Mummichog
    },
    blackNoseDace()
    {
        this.BlackNoseDace = !this.BlackNoseDace
    },
    tomcod()
    {
        this.Tomcod = !this.Tomcod
    },
    count: function(county, fish)
    {
        var x
        for(var i in this.fishData)
        {
            if ((this.fishData.county[i] == county)&&(this.fishData.species_common_name[i] == fish))
            {
                x++
            }
        }
        return x
    }
    

  },
  beforeMount(){
    this.getFishData()
  }  
}
</script>