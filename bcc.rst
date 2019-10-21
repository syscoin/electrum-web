Statement regarding ElectrumSys and Bitcoin Cash
=============================================

July 26th, 2017.

ElectrumSys is a Syscoin wallet created by Thomas Voegtlin in 2011.
ElectrumSys is distributed by ElectrumSys Technologies GmbH, a company
registered in Germany, using the website https://electrum.syscoin.org


Multiple chain validation
-------------------------

ElectrumSys is a SPV wallet, which means that it verifies and stores a
sequence of block headers sent by the Bitcoin network, and uses these
headers to verify that transactions are in the Bitcoin blockchain.

A new feature in ElectrumSys 2.9 is Multiple Chain Validation
(MCV). Instead of validating a single sequence of block headers,
ElectrumSys 2.9 validates a tree of headers, sent by ElectrumSys servers
that may follow different branches of a fork in the Bitcoin
blockchain.

The purpose of MCV is to detect blockchain forks that would otherwise
be invisible to the classical SPV model, and to let users choose
between branches of such a fork. In particular, this feature has been
designed for the BIP148 soft fork, or for the Segwit2x block size
increase.

However, 'Multiple Chain Validation' still includes 'Validation'. In
particular, it assumes that both branches of a fork are valid from the
perspective of a SPV wallet, because they both follow the Bitcoin
rules.

Bitcoin Cash (BCC) is a hard fork that changes the difficulty rules of
Bitcoin. Therefore, SPV wallets written for Bitcoin will reject the
block headers of a BCC fork, and so will ElectrumSys. This means that
ElectrumSys will reject block headers sent by ElectrumSys server running
Bitcoin Cash, and that users will not be able to send and receive BCC
using ElectrumSys.


Would it be possible to add support for Bitcoin Cash in ElectrumSys?
-----------------------------------------------------------------

Yes, it would be possible to support BCC in ElectrumSys, by modifying the
difficulty rules we use for block headers validation, and the
transaction creation rules. There are already forks of ElectrumSys doing
that.

However, the headers validation rules of BCC are strictly less secure
than those of Bitcoin. Therefore, it would not be possible to use the
same rules for both chains in ElectrumSys, without significantly lowering
the security of validation of legit Bitcoin transactions.

Thus, in order to safely support both Bitcoin and BCC in the same
ElectrumSys client, one would need to implement two separate sets of
headers validation rules. This is clearly out of the scope of multiple
chain validation. Again, the purpose of MCV is to protect users from
blockchain forks that are not detectable by the classical SPV model,
such as a block size increase.


How to redeem my BCC?
---------------------

BCC wallets will require you to import your seed or your private keys,
which can be exported from ElectrumSys. Doing so will expose all your
Bitcoin funds associated with that seed to the BCC wallet you decide
to use.

Therefore, *after* the BCC fork, but *before* you enter a seed or
private key in a BCC wallet, you should move all your funds to a new
ElectrumSys wallet, with a new seed. You will still be able to use the
old seed or private key with BCC, because BCC has replay
protection. Wait until your funds are confirmed in your new Bitcoin
wallet, before you enter the old private key in a BCC wallet. This
will protect your BTC funds from rogue/untrusted software.


About ElectrumSys Cash
-------------------

The name "ElectrumSys" has been visible on bitcoincash.org and
electrumsyscash.org, with a modified version of our logo. The use of our
name and of our logo constitutes a trademark infringement.

We have never enforced our trademark against altcoin versions of
ElectrumSys (such as Litecoin, etc), because we consider that users of
these altcoins are well aware of the distinction between Bitcoin and
their coin, and that they cannot be harmed by that confusion. However,
we do not agree with the use of the ElectrumSys name in the context of a
Bitcoin fork, because it suggests that we endorse that fork, and that
we also endorse that wallet.

We reserve ourselves the right to use the name ElectrumSys for a Bitcoin
Cash wallet, should we decide to publish one in the future.
